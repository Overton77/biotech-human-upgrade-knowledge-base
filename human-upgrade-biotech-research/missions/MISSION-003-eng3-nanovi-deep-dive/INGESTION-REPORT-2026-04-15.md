# Ingestion report — MISSION-003 Eng3 / NanoVi (2026-04-15)

GraphQL server: `humanupgrade-graphql` (MCP `project-0-humanupgradeapp-humanupgrade-graphql`). Embeddings: `EmbeddingWriteMode` **AUTO** on all create/update mutations that accept `embedding`.

## Episode

| Field | Value |
|-------|--------|
| Resolved by | `episode(episodePageUrl: "https://daveasprey.com/1335-rowena-gates-eng3/")` |
| DB slug | `human-upgrade-1335-rowena-gates-eng3` |
| Action | `updateEpisode` → `guests.connect`: **Rowena Gates** (`rowena-gates`) |

## Created

### People

- **hans-eng** — Hans Eng (Founder and CEO); bio from official leadership / company-foundations notes.
- **rowena-gates** — Rowena Gates (Principal, VP Business Development); bio from official leadership and mission seed context.

### Organization

- **eng3-corporation** — Eng3 Corporation (`MANUFACTURER`): description, `websiteUrl` https://eng3corp.com, headquarters Seattle, founded 2003, domains `eng3corp.com` + `eng3.com`, tags and aliases as ingested.

### Organization relations

- **owners.connect**: `hans-eng`
- **executives.connect**: `hans-eng`, `rowena-gates`

### Products (all `organizationId` → Eng3; `isLabTestPanelDefinition`: false)

| Slug | SKU | Notes |
|------|-----|--------|
| nanovi-eco | 4650-00 | Home entry tier; long-form description + categories/benefits |
| nanovi-pro | 4800-00 | Mid tier; smartcard / clinic positioning |
| nanovi-exo | 4900-00 | Flagship tier; performance positioning |

### Case studies

- **cohu-enzyme-activity-pmid-35054784** — IJMS mechanistic paper (DOI 10.3390/ijms23020601); PubMed URL; long `fullTextSummary` / `outcomeSummary` reflecting in vitro scope and Eng3 marketing context.
- **nct03630419-mito-food-plan-cell-repair** — NCT03630419; ClinicalTrials.gov URL; registry-centered `fullTextSummary`; sponsor named in text as Perseverance Research Center, LLC (not Eng3).

### Case study ↔ organization

- Both studies: `updateCaseStudy` → `referencedByOrganizations.connect`: **eng3-corporation** (company cites / aligns with these evidence objects; neither study is Eng3-sponsored, so **businessSponsors** was not used for Eng3).

## Intentionally omitted

- **Lab tests / biomarkers** — Mission centers on hardware devices and published trials/papers; no lab panel entities in `04-entities/`.
- **containsCompounds** — No compound-level ontology in mission materials (devices, not supplements).
- **Separate “NanoVi” organization** — Treated as Eng3’s product brand; products hang off **eng3-corporation** per entity notes (`organizationId: eng3-corporation`).
- **Perseverance Research Center, LLC** — Not created; only referenced inside NCT narrative. Add later if you want sponsor-level linking via `businessSponsors`.

## Sources used (vault)

- `00-inbox/MISSION-003-eng3-nanovi-deep-dive.md`
- `04-entities/organizations/eng3-corporation.md`
- `04-entities/products/nanovi-*.md`
- `04-entities/studies/*.md`
- `03-syntheses/eng3-nanovi-synthesis.md`
- `01-sources/markdown/company-foundations.md` (leadership detail)

## Gaps / follow-ups

1. **Episode record** — Title in DB is generic (`Human Upgrade Episode`); enriching title/summary from podcast CMS or seed file is a content pipeline task, not done here to avoid unnecessary search-field churn.
2. **Distributor domains** (e.g. `nanovi.de`) — Mission flags as unresolved; no separate org rows created.
3. **Athletic / HRV / immune claims** — Largely company-summary-grade in the mission; not ingested as separate case studies.
4. **Hans Eng as episode guest** — Episode guest is Rowena per mission YAML; Hans is linked on the organization only.

## Verification queries (examples)

```graphql
query {
  episode(episodePageUrl: "https://daveasprey.com/1335-rowena-gates-eng3/") {
    slug
    guests { slug fullName }
  }
  organization(slug: "eng3-corporation") {
    owners { slug }
    executives { slug }
  }
}
```
