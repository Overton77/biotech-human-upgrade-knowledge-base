---
name: graphql-ingestion
description: |
  Ingest research entities into the Human Upgrade PostgreSQL database via the humanupgrade-graphql MCP server. Create and connect persons, organizations, products, compounds, case studies, media, and other entities. Use when the user says "ingest", "seed database", "create in database", "push to GraphQL", "connect entities", or when research is mature enough for structured database storage.
---

# GraphQL Database Ingestion

## MCP Server

**Name:** `humanupgrade-graphql` (project-0-humanupgradeapp-humanupgrade-graphql)

This MCP server exposes typed tools for every CRUD operation. Use the tool names directly — they map to GraphQL mutations.

## Entity Types & Tools

| Entity | Create | Update | Delete | Get One | Get Many |
|--------|--------|--------|--------|---------|----------|
| Person | `CreatePerson` | `UpdatePerson` | `DeletePerson` | `GetPerson` | `GetPersons` |
| Organization | `CreateOrgadc96211` | `UpdateOrgac24098b` | `DeleteOrgaa7ea9fb` | `GetOrganization` | `GetOrganizations` |
| Product | `CreateProduct` | `UpdateProduct` | `DeleteProduct` | `GetProduct` | `GetProducts` |
| Compound | `CreateCompound` | `UpdateCompound` | `DeleteCompound` | `GetCompound` | `GetCompounds` |
| CaseStudy | `CreateCaseStudy` | `UpdateCaseStudy` | `DeleteCaseStudy` | `GetCaseStudy` | `GetCaseStudies` |
| Media | `CreateMedia` | `UpdateMedia` | `DeleteMedia` | `GetMedia` | — |
| Episode | `CreateEpisode` | `UpdateEpisode` | `DeleteEpisode` | `GetEpisode` | `GetEpisodes` |
| Claim | `CreateClaim` | `UpdateClaim` | `DeleteClaim` | `GetClaim` | `GetClaims` |
| Podcast | `CreatePodcast` | `UpdatePodcast` | `DeletePodcast` | `GetPodcast` | `GetPodcasts` |
| LabTest | `CreateLabTest` | `UpdateLabTest` | `DeleteLabTest` | `GetLabTest` | `GetLabTests` |
| Biomarker | `CreateBiomarker` | `UpdateBiomarker` | `DeleteBiomarker` | `GetBiomarker` | `GetBiomarkers` |

Use `introspect` and `search` tools to explore the schema. Use `validate` before `execute` for raw queries.

## Ingestion Workflow

### Step 1: Create Base Entities (no relations)

Create entities in dependency order — entities that others reference first:

1. **Persons** — no dependencies
2. **Organizations** — no dependencies
3. **Compounds** — no dependencies
4. **Products** — pass `organizationId` at creation time if known
5. **CaseStudies** — no dependencies
6. **Episodes** — requires `podcastId`

### Step 2: Connect Relations (update mutations)

After all entities exist, wire up many-to-many and ownership relations:

**Organization → People:**
```json
UpdateOrganization(where: {slug: "org-slug"}, data: {
  owners: { connect: [{slug: "person-slug"}] },
  executives: { connect: [{slug: "person-slug"}] }
})
```

**Product → Compounds:**
```json
UpdateProduct(where: {slug: "product-slug"}, data: {
  containsCompounds: { connect: [{slug: "compound-1"}, {slug: "compound-2"}] }
})
```

**CaseStudy → Organizations:**
```json
UpdateCaseStudy(where: {slug: "study-slug"}, data: {
  referencedByOrganizations: { connect: [{slug: "org-slug"}] },
  businessSponsors: { connect: [{slug: "sponsor-slug"}] }
})
```

**Episode → Guests/Sponsors:**
```json
UpdateEpisode(where: {slug: "episode-slug"}, data: {
  guests: { connect: [{slug: "person-slug"}] },
  sponsorOrganizations: { connect: [{slug: "org-slug"}] }
})
```

### Step 3: Add Media

Create media records linked to entities via their ID fields:

```json
CreateMedia(data: {
  url: "https://...",
  type: "IMAGE",  // IMAGE | VIDEO | AUDIO | DOCUMENT | LINK | OTHER
  title: "Description",
  altText: "Accessibility text",
  sortOrder: 0,
  personId: "cuid...",       // OR
  organizationId: "cuid...", // OR
  productId: "cuid...",      // OR
  compoundId: "cuid...",     // OR
  caseStudyId: "cuid..."     // etc — one FK per media record
})
```

## Relation Operation Syntax

All many-to-many relations use `ToManyRelationOperationInput`:

```json
{
  "connect": [{"slug": "a"}, {"slug": "b"}],   // Add relations
  "disconnect": [{"slug": "c"}],                // Remove relations
  "set": [{"slug": "a"}, {"slug": "b"}]         // Replace all relations
}
```

All to-one relations use `ToOneRelationOperationInput`:

```json
{
  "connect": {"slug": "org-slug"},   // Set relation
  "disconnect": true                  // Clear relation
}
```

Nullable scalar fields use `StringNullableOperationInput`:

```json
{ "set": "new value" }   // Set value
{ "clear": true }        // Set to null
```

String arrays use `StringListOperationInput`:

```json
{ "set": ["a", "b"] }        // Replace entire array
{ "add": ["c"] }             // Append
{ "remove": ["a"] }          // Remove
```

## Key Relationships (Prisma Schema)

```
Organization ──< Product (organizationId FK)
Product >──< Compound (implicit many-to-many: containsCompounds/products)
Organization >──< Person (owners, executives — two separate relations)
Organization >──< CaseStudy (referencedCaseStudies, businessSponsoredCases)
Episode >──< Person (guests)
Episode >──< Organization (sponsorOrganizations)
Episode ──< Claim (episodeId FK)
Claim >── Person (speaker — optional to-one)
Product ──< LabTest (productId FK)
LabTest >──< Biomarker (testsBiomarkers)
Compound >──< Biomarker (CompoundBiomarkerAssociations)
Media → any entity (one FK field per media record)
```

## Verification Query

After ingestion, verify connections with a raw GraphQL query:

```graphql
query {
  organizations {
    name
    owners { fullName }
    executives { fullName }
    products {
      name
      containsCompounds { name canonicalName }
    }
    referencedCaseStudies { title doi }
    businessSponsoredCases { title }
  }
}
```

Use the `execute` tool to run raw queries.

## Data Quality Rules

1. **Slugs must be unique** per entity type — use kebab-case
2. **Always check if entity exists** before creating (use Get tools) to avoid duplicates
3. **Create before connecting** — all referenced entities must exist before relation operations
4. **One media record per asset** — link to exactly one entity via its FK field
5. **Preserve provenance** — include sourceUrl, doi, journal on CaseStudies
6. **Use tags consistently** — lowercase, hyphenated, domain-relevant

## Ingestion from Vault Notes

When ingesting from the Obsidian vault (`obsidian-vault-research` skill):

1. Read entity notes from `04-entities/` — frontmatter has slug, name, type
2. Read ingestion data from `02-research/graphql-ingestion-*.md` — has JSON payloads
3. Create entities using the JSON payloads
4. Connect relations using slugs from the vault notes
5. Add media from scraped image URLs
6. Verify with a query
7. Update the vault ingestion note with completion status
