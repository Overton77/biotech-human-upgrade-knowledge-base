---
name: graphql-ingestion
description: |
  Ingests research into the Human Upgrade database via the humanupgrade-graphql MCP server. Emphasizes update mutations (where, data, embedding with EmbeddingWriteMode AUTO), relation wiring via connect, connectOrCreate, create, set, disconnect, SearchMode NONE pre-checks, and canonical schema/operations paths. Use when the user says ingest, seed, push to GraphQL, attach relationships, or provides mission files for database ingestion.
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
| Media ↔ parent | Parent’s `update*` | `media` on org/product/person/episode/claim/case study/podcast/etc., **or** `CreateMedia` with a single parent FK |

`OrganizationUpdateInput` does **not** include `products` or `caseStudies` — link from **product** and **case study** updates (or FKs on create) as above.

**Compound ↔ biomarker** edges are not on `CompoundUpdateInput` / `BiomarkerUpdateInput`; use **lab test** and **product** relation fields as appropriate.

---

## Discovery before ingest (`SearchMode`)

Plural queries take `input` with `mode: SearchMode` (`NONE` | `LEXICAL` | `SEMANTIC` | `HYBRID`).

- **`mode: NONE`** — Filter/list without search scoring; use **before ingest** to see what exists (`limit` / `offset` + type-specific filters).
- Other modes — Supply `query` for text search as needed.

Singular queries use `id` / `slug` per `*WhereUniqueInput` (not arbitrary `name` uniqueness).

---

## Media

- **`CreateMedia`:** Set at most one of `podcastId`, `episodeId`, `claimId`, `personId`, `organizationId`, `productId`, `compoundId`, `labTestId`, `biomarkerId`, `caseStudyId`.
- **`UpdateMedia`:** Metadata only in `MediaUpdateInput` (no parent FKs). Re-parent via parent **`media`** relation ops or delete + recreate.

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
4. Media: **`CreateMedia`** or parent **`media`** nested in **`update*`**.
5. Verify with **`execute`** queries; match field selection to what you need.

Mission-specific files and paths the user provides override generic folder guesses.
