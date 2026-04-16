# MISSION-005 ingestion report — 2026-04-15

GraphQL target: Human Upgrade API via MCP `project-0-humanupgradeapp-humanupgrade-graphql` (humanupgrade-graphql). Embeddings: `AUTO` on all mutations that accept `embedding`.

## Episode resolution

- **Mission file URL:** `https://daveasprey.com/1225-timeline-anurag-singh/`
- **Resolved episode:** `id` `cmo0kcequ08oau8o2qlymoqkt`, slug `human-upgrade-1257`, **episodeNumber 1257** (mission YAML still references episode string `"1225"`; DB canonical numbering differs while `episodePageUrl` matches).
- **Guest:** `updateEpisode` → `guests.connect` → **Anurag Singh** (`anurag-singh`). Verified query shows guest attached.

## Created

| Entity | Slug | Notes |
|--------|------|--------|
| Organization | `timeline-amazentis` | BRAND; description, website, domains, tags, aliases from `04-entities/organizations/timeline-amazentis.md` + mission synthesis. |
| Person | `anurag-singh` | CMO; bio/title/expertise from people entity + mission context. |
| Compound | `urolithin-a` | PubChem/CAS/mechanisms from compound entity. |
| Product | `timeline-mitopure-gummies` | Pricing, format, claims, URL from product note. |
| Product | `timeline-mitopure-softgels` | Same. |
| Product | `timeline-mitopure-powder` | Same. |
| Product | `timeline-mitopure-firming-serum` | Skincare; price $225 from vault. |
| Case study | `pmid-32694802-urolithin-a-first-human` | Nature Metabolism; FIHP-style trial. |
| Case study | `pmid-35050355-urolithin-a-older-adults` | JAMA Network Open; older-adult RCT. |
| Case study | `pmid-35584623-urolithin-a-middle-aged-adults` | Cell Reports Medicine; NCT03464500 in tags/summary. |
| Case study | `pmid-41174221-urolithin-a-immune-aging` | Nature Aging; NCT05735886 / PMC in tags. |

## Updated (relationships)

| Mutation | Detail |
|----------|--------|
| `updateOrganization` | `executives.connect` → `anurag-singh`. |
| `updateProduct` ×4 | `containsCompounds.connect` → `urolithin-a` (oral + serum all list Mitopure / UA as active). |
| `updateCaseStudy` ×4 | `businessSponsors.connect` → `timeline-amazentis` (mission-classified company-linked human trials; not used for independent third-party citations). |
| `updateEpisode` | `guests.connect` → `anurag-singh`. |

## Sources used (vault)

Primary: `04-entities/` (organization, person, products, compound, studies). Supporting: `00-inbox/MISSION-005-timeline-mitopure-deep-dive.md`, `03-syntheses/timeline-mission-synthesis.md`, `02-research/` and `01-sources/markdown/` as cited in entity notes.

## Gaps / follow-ups

1. **Episode numbering:** Align mission YAML episode label `"1225"` with CMS episode number **1257** or document that slug/title numbering is source-of-truth vs marketing URL segment.
2. **Corporate structure:** Exact legal stack Timeline / Timeline Longevity / Amazentis SA remains unverified; `legalName` stored as explicitly qualified in org create.
3. **Partners not ingested as orgs:** Nestlé Health Science and L’Oréal appear in research as investors/partners; no separate `Organization` rows created—add if sponsor linking to episodes or case studies is required.
4. **Skincare catalog:** Mission only ingested **Firming Serum** as a full product entity; other Mitopure skincare SKUs were out of detailed entity capture.
5. **Case study `referencedByOrganizations`:** Left empty; all four studies were treated as sponsor-affiliated human evidence. If JAMA/Cell/Nature journals should appear as reference organizations, schema/product policy should clarify.
6. **Publish pipeline:** Episode `publishStatus` remained `HIDDEN` / `isPublished` false—ingestion did not change publish flags.

## Schema / data hygiene

- `ProductCreateInput.organizationId` used as internal organization **id** string returned from `createOrganization`.
- PMID and NCT encoded in case study `tags`, `keywords`, `sourceUrl`, `doi`, and narrative fields where applicable.
