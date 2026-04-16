---
name: graphql-ingestion
description: |
  Ingests research into the Human Upgrade database via the humanupgrade-graphql MCP server. Emphasizes update mutations (where, data, embedding with EmbeddingWriteMode AUTO), relation wiring via connect, connectOrCreate, create, set, disconnect—including nested media.create on parent updates—SearchMode NONE pre-checks, and canonical schema/operations paths. Use when the user says ingest, seed, push to GraphQL, attach relationships, or provides mission files for database ingestion.
---

# GraphQL database ingestion

## Canonical sources (read these)

| Resource | Path |
|----------|------|
| **Full schema** | [`humanupgradeapi/src/graphql/schema.graphql`](../../../../humanupgradeapi/src/graphql/schema.graphql) |
| **Saved operations** (queries/mutations as the API expects them) | [`humanupgradeapi/src/graphql/operations/`](../../../../humanupgradeapi/src/graphql/operations/) — subfolders: `organizations/`, `products/`, `caseStudies/`, `episodes/`, `claims/`, `persons/`, `compounds/`, `labTests/`, `biomarkers/`, `media/`, `podcasts/`, etc. |

Use **`introspect`** on `Mutation` / `Query` (humanupgrade-graphql MCP) to confirm signatures after schema changes. Prefer **`validate`** then **`execute`** for one-off operations. Example on-disk mutations: `operations/caseStudies/UpdateCaseStudy.graphql` shows the exact **`where` / `data` / `embedding`** variable shape.

---

## Update mutations (primary place for relationships)

Every **entity update** follows the same GraphQL shape (verified against live schema introspection):

```graphql
updateExample(
  where: ExampleWhereUniqueInput!
  data: ExampleUpdateInput!
  embedding: EmbeddingWriteOptionsInput   # optional; see below
): Example!
```

- **`where`** — Identifies the row: usually `{ slug: "…" }` or `{ id: "…" }` per `*WhereUniqueInput` (`ClaimWhereUniqueInput` is `{ id: ID! }` only).
- **`data`** — Scalar patches **and** nested relation operations. **This is where relationships are attached or removed:** `connect`, `connectOrCreate`, `create`, `set`, `disconnect` on the fields defined on that type’s `*UpdateInput` (e.g. `OrganizationUpdateInput.owners`, `ProductUpdateInput.containsCompounds`, `CaseStudyUpdateInput.referencedByOrganizations`).
- **`embedding`** — Controls embedding writes for that mutation. Type: `EmbeddingWriteOptionsInput` → `{ mode: EmbeddingWriteMode }`.

### `EmbeddingWriteMode` (usually AUTO)

Defined in the schema (`EmbeddingWriteMode` enum). **`embedding`’s `mode` defaults to `AUTO`** if the argument is omitted.

| Mode | When to use |
|------|----------------|
| **AUTO** | **Default for ingestion.** Let the API decide when to (re)generate embeddings after this write. Omit `embedding` or pass `{ "mode": "AUTO" }`. |
| **SKIP** | Do not write embeddings for this mutation (batch or maintenance scenarios). |
| **FORCE** | Recompute embeddings for affected content after this update. |

**Practice:** For normal ingest/connect flows, **omit `embedding` or set `mode: AUTO`**. Do not invent other embedding shapes.

### Relation ops inside `data`

Relation fields use the shared inputs from the schema (e.g. `PersonToManyRelationUpdateInput`, `OrganizationToManyRelationUpdateInput`, `CompoundToManyRelationUpdateInput`, `MediaToManyRelationUpdateInput`, `PersonToOneRelationUpdateInput`).

**To-many:** `set`, `connect`, `disconnect`, `create`, `connectOrCreate` (see schema for each).

**To-one:** `connect`, `disconnect: true`, `create`, `connectOrCreate`.

**Scalars / lists:** `StringNullableOperationInput` (`set` / `clear`), `StringListOperationInput` (`set` / `add` / `remove`), etc.

---

## Create mutations

Shape (entities that support embeddings):

```graphql
createExample(
  data: ExampleCreateInput!
  embedding: EmbeddingWriteOptionsInput
): Example!
```

- **`data`** — Model fields and direct FKs only (e.g. `organizationId` on `ProductCreateInput`, `podcastId` on `EpisodeCreateInput`). No nested relation graphs on create inputs.
- **`embedding`** — Same semantics as updates; **default / usual choice is AUTO or omitted.**

**Exception — Media:** `createMedia(data: MediaCreateInput!): Media!` has **no** `embedding` argument.

---

## Mutations without `embedding`

| Operation | Arguments |
|-----------|-----------|
| **`createMedia`** | `data` only |
| **`updateMedia`** | `where`, `data` only |
| **`deleteMedia`** | `where` only |
| **All `delete*`** | `where` only |

For these, there is no `EmbeddingWriteMode` on the mutation itself.

---

## Where to update which relationship

| Intent | Mutation | Relation fields in `data` (see schema) |
|--------|----------|----------------------------------------|
| Organization ↔ people | `updateOrganization` | `owners`, `executives` |
| Organization ↔ products | `updateProduct` (or `organizationId` / `createProduct`) | `organization` (to-one) on **product** |
| Organization ↔ case studies | `updateCaseStudy` | `referencedByOrganizations`, `businessSponsors` |
| Product ↔ compounds | `updateProduct` | `containsCompounds` |
| Lab test ↔ biomarkers | `updateLabTest` | `testsBiomarkers` |
| Lab test ↔ product / org | `updateLabTest` | `product`, `organization` |
| Episode ↔ people | `updateEpisode` | `guests` |
| Episode ↔ organizations | `updateEpisode` | `sponsorOrganizations` |
| Claim ↔ speaker | `updateClaim` | `speaker` (to-one) |
| Media ↔ parent | Parent’s `update*` (see **Media** below) or `createMedia` | `media` with `connect` / `create` / `connectOrCreate`, **or** standalone `createMedia` with exactly one parent FK |

`OrganizationUpdateInput` does **not** include `products` or `caseStudies` — link from **product** and **case study** updates (or FKs on create) as above.

**Compound ↔ biomarker** edges are not on `CompoundUpdateInput` / `BiomarkerUpdateInput`; use **lab test** and **product** relation fields as appropriate.

---

## Discovery before ingest (`SearchMode`)

Plural queries take `input` with `mode: SearchMode` (`NONE` | `LEXICAL` | `SEMANTIC` | `HYBRID`).

- **`mode: NONE`** — Filter/list without search scoring; use **before ingest** to see what exists (`limit` / `offset` + type-specific filters).
- Other modes — Supply `query` for text search as needed.

### Plural list shape (`*SearchHit` — easy to get wrong)

Each plural field returns something like `OrganizationSearchResult { items, total }`, but **`items` is not `Organization[]`**. Each element is a **`*SearchHit`** (e.g. `OrganizationSearchHit`) that wraps the row plus optional scores:

- Select the **nested entity field** for that type: `organization { id slug name … }`, `person { … }`, `product { … }`, `caseStudy { … }`, `compound { … }`, etc.
- Do **not** query `id` / `slug` / `name` directly on the hit; GraphQL will reject those fields. Optional: `lexicalScore`, `semanticScore`, `hybridScore` on the hit when present.

Example (dedupe before ingest):

```graphql
query {
  organizations(input: { mode: NONE, limit: 50, offset: 0 }) {
    total
    items {
      organization { id slug name organizationType }
    }
  }
}
```

Singular queries use `id` / `slug` per `*WhereUniqueInput` (not arbitrary `name` uniqueness).

---

## Media

### Standalone `createMedia`

- **`createMedia(data: MediaCreateInput!)`** — Set **at most one** of `podcastId`, `episodeId`, `claimId`, `personId`, `organizationId`, `productId`, `compoundId`, `labTestId`, `biomarkerId`, `caseStudyId` so the new row is linked to its parent.
- No `embedding` argument.

### Nested `media` on parent `update*` (additive creates)

Types that expose `media: MediaToManyRelationUpdateInput` (e.g. `OrganizationUpdateInput`, `PersonUpdateInput`, `ProductUpdateInput`, `EpisodeUpdateInput`, `ClaimUpdateInput`, `CaseStudyUpdateInput`, `PodcastUpdateInput`, etc.) accept the same relation ops as other to-many fields:

| Op | Use for ingestion |
|----|-------------------|
| **`create`** | Append new `Media` rows while updating the parent. Each element is a `MediaCreateInput`. |
| **`connect`** | Link existing media by `{ id }` only (`MediaWhereUniqueInput`). |
| **`connectOrCreate`** | `where` is `{ id }` only; `create` supplies `MediaCreateInput` if no row with that id exists. |
| **`disconnect`** | Unlink by `{ id }`. |
| **`set`** | **Replaces** the entire media set for that parent. Avoid unless you intentionally mean “make this list the only media.” |

**Nested `create` semantics (important):** On parent updates, the API maps nested `media.create` through a sanitizer that **keeps only media scalars** (`url`, `type`, optional `mimeType`, `title`, `altText`, `caption`, dimensions, `durationSeconds`, `fileSizeBytes`, `sortOrder`). **Parent foreign keys on each `MediaCreateInput` are not used**—the parent is implied by whichever `updateOrganization` / `updatePerson` / `updateProduct` / … mutation you called. Prefer omitting those FKs in nested `create` payloads for clarity.

**Example — add two images to an organization in one mutation:**

```graphql
updateOrganization(
  where: { slug: "example-org" }
  data: {
    media: {
      create: [
        { url: "https://...", type: IMAGE, title: "Logo", sortOrder: 0 }
        { url: "https://...", type: IMAGE, title: "Team photo", sortOrder: 1 }
      ]
    }
  }
) { id slug }
```

**`createMedia` vs nested `media.create`:** Functionally both attach new media to a parent. Use **`createMedia`** when you only need to insert media (and have the parent id or slug resolved elsewhere). Use **`update*`** with **`media.create`** when you are already patching the parent and want a single transactional update.

### `updateMedia` / re-parenting

- **`updateMedia`:** Metadata only in `MediaUpdateInput` (no parent FKs). To change which entity owns a row, use the parent’s **`media`** relation (`connect` / `disconnect` / `set`) or delete + recreate.

---

## MCP tools

| Tool | Role |
|------|------|
| `introspect` | Types (`Query`, `Mutation`, `*UpdateInput`, …) |
| `search` | Find type names by keyword |
| `validate` / `execute` | Ad-hoc operations |
| `Create*`, `Update*`, `Get*`, … | Typed wrappers matching operations under `operations/` |

---

## Ingestion order (summary)

1. Plural **`mode: NONE`** (or singular by **slug**) to dedupe.
2. **`create*`** base rows (`embedding` AUTO or omitted).
3. **`update*`** with **`data`** relation ops (`embedding` AUTO or omitted); use **`where`** for stable ids/slugs.
4. Media: **`createMedia`** or parent **`update*`** → **`data.media.create`** / **`connect`** (see **Media**); avoid **`media.set`** unless replacing the full list.
5. Verify with **`execute`** queries; match field selection to what you need.

Mission-specific files and paths the user provides override generic folder guesses.
