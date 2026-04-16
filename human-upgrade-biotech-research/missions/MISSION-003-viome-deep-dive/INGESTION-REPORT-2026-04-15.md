# GraphQL ingestion report — MISSION-003 Viome deep dive

**Date:** April 15, 2026  
**Target API:** Human Upgrade GraphQL (`humanupgrade-graphql` MCP)  
**Embedding mode:** `AUTO` on all mutations that support `EmbeddingWriteOptionsInput` (per ingestion policy).

---

## What was ingested

### Organization

| Slug | Action | Notes |
|------|--------|--------|
| `viome-life-sciences` | **Create** | `OrganizationType: BRAND`, legal name, long description, website, domains (`viome.com`, `viomelifesciences.com`, `cancerdetect.viome.com`), tags, aliases. |

**Source material:** `04-entities/organizations/viome-life-sciences.md`, plus synthesis and company research (`03-syntheses/viome-synthesis.md`, `02-research/company/company-foundations.md`) for domains and leadership context.

### People

| Slug | Action | Role on org |
|------|--------|-------------|
| `naveen-jain` | **Create** | `owners` + `executives` |
| `guruduth-banavar` | **Create** | `executives` only |
| `momo-vuyisich` | **Create** | `executives` only |

**Source material:** `04-entities/people/naveen-jain.md`; Banavar and Vuyisich from `02-research/company/company-foundations.md` (named leadership), not separate entity files.

### Products (lab test catalog)

All created with `organizationId` pointing to Viome, `isLabTestPanelDefinition: true`, pricing/URLs/categories/benefits from entity notes.

| Slug | Name |
|------|------|
| `gut-intelligence` | Gut Intelligence |
| `full-body-intelligence` | Full Body Intelligence |
| `oral-health-intelligence` | Oral Health Intelligence |
| `cancerdetect-oral-throat` | CancerDetect Oral & Throat |

**Source material:** `04-entities/products/*.md` and `02-research/products/product-catalog.md` where relevant.

### Lab tests

Four panel records, each linked to **organization** and **product** via create inputs / relations.

| Slug | Linked product slug |
|------|---------------------|
| `viome-gut-intelligence-panel` | `gut-intelligence` |
| `viome-full-body-intelligence-panel` | `full-body-intelligence` |
| `viome-oral-health-intelligence-panel` | `oral-health-intelligence` |
| `viome-cancerdetect-oral-throat-panel` | `cancerdetect-oral-throat` |

**Biomarkers:** Connected via `updateLabTest` → `testsBiomarkers.connectOrCreate` using composite / pathway-style slugs (e.g., metatranscriptome layers, Viome score bundles, CDOT classifier signals). No separate compound graph was added; mission products are diagnostic panels, not ingredient lists.

### Case studies

Eight records: four PubMed-indexed papers + four ClinicalTrials.gov registrations.

| Slug | Type |
|------|------|
| `pmid-37454545-cdot-oral-throat-cancer` | Peer-reviewed (CDOT) |
| `pmid-40128554-synthetic-controls-metatranscriptomic-clinical-test` | Peer-reviewed (QC / synthetic controls) |
| `pmid-36622006-saliva-metatranscriptome-test` | Peer-reviewed (saliva MT methods) |
| `pmid-32772558-capillary-blood-transcriptome` | Peer-reviewed (blood transcriptome methods) |
| `nct06174428-validity-oral-throat-cancer-test` | Registry |
| `nct05451303-oralviome-cancer-testing-system` | Registry |
| `nct05465616-precision-nutrition-hba1c` | Registry |
| `nct05972330-vrx-mybiotics-oral-lozenges` | Registry |

**Relationships:** All eight attached to Viome with **`businessSponsors`** → `viome-life-sciences` (organization **`businessSponsoredCases`**). Nothing was placed under **`referencedCaseStudies`** / **`referencedByOrganizations`** because these records are sponsor-led or company-authored; “reference-only” independence was not asserted.

**Source material:** `04-entities/studies/*.md`; **`fullTextSummary`** was later enriched using ClinicalTrials.gov API v2 JSON and PubMed abstracts (see prior pass).

### Episode link

- **Episode resolved by:** `episodePageUrl` = `https://daveasprey.com/1228-viome-naveen-jain/`  
- **Guest attached:** `naveen-jain` via `updateEpisode` → `guests.connect`.

**Note:** The database episode row may show a different internal episode number than the URL segment (`1228`); ingestion used **`episodePageUrl`** as the stable key per mission instructions.

---

## Media enrichment (April 15, 2026 follow-up)

Public image URLs were discovered with **Tavily** (`tavily_search`, `include_images: true`, `include_image_descriptions: true`) and attached via **`createMedia`** on the **humanupgrade-graphql** MCP (parent FK on `MediaCreateInput`).

| Entity (slug) | Media title | Notes |
|---------------|-------------|--------|
| `viome-life-sciences` | Viome Life Sciences wordmark (press) | PR Newswire-hosted logo JPG |
| `naveen-jain` | Naveen Jain (public appearance) | Wikimedia Commons (CC BY-SA 2.0), Tech Cocktail Week 2013 |
| `guruduth-banavar` | Guruduth Banavar headshot | Viome official CMS (`strapi.azure.viome.com`) |
| `momo-vuyisich` | Momo Vuyisich (conference speaker) | PMWC speaker image |
| `gut-intelligence` | Gut Intelligence test kit | Viome CMS product art |
| `full-body-intelligence` | Full Body Intelligence test kit | Viome CMS product art |
| `oral-health-intelligence` | Oral Health Intelligence test kit | Viome CMS product art |
| `cancerdetect-oral-throat` | CancerDetect Oral & Throat kit | Viome / CancerDetect CMS product art |

---

## Data lineage (mission → API)

| Layer | Path |
|-------|------|
| Mission definition | `00-inbox/MISSION-003-viome-deep-dive.md` |
| Primary entity facts | `04-entities/` (organizations, people, products, studies) |
| Supporting narrative | `02-research/`, `03-syntheses/`, `01-sources/markdown/` |

---

## Gaps and completeness (current state)

- **Products not modeled as separate product rows:** Precision Supplements, VRx My·Biotics lines were discussed in research notes but not created as `Product` rows in this pass.
- **People:** Only three people ingested; other named executives/advisors in `company-foundations.md` were not created.
- **Compounds:** `containsCompounds` on products was intentionally not populated; supplement chemistry was out of scope for this mission’s entity set.
- **Biomarkers:** Represented as interpretive/composite slugs aligned to the mission narrative, not a full public biomarker inventory (Viome score-to-feature mapping is partly proprietary per mission notes).
- **Case studies — registry results:** At ingestion time, ClinicalTrials.gov **results** were not posted for these NCTs; evidence strength remains protocol + publications where applicable.
- **Episode sponsorship:** Viome was **not** added under `episode.sponsorOrganizations` (only guest linkage was requested).

---

## Recommendations — schema

1. **Registry vs publication split:** Consider optional fields (or tags) such as `evidenceSource: REGISTRY | PEER_REVIEW | PREPRINT`, `registryId` (NCT), `resultsPosted: Boolean` (synced from ClinicalTrials.gov when available), to make embedding and UI behavior explicit.
2. **Trial–product links:** A structured link from `CaseStudy` (NCT) to `Product` or `LabTest` when a trial explicitly names an intervention (e.g., VRx lozenges) would reduce ambiguity versus free-text `fullTextSummary`.
3. **Mission provenance:** Optional `ingestedFromMissionId` or external ref on create/update could round-trip vault missions without overloading `tags`.
4. **Person–role typing:** Distinguish `OWNER` vs `EXECUTIVE` vs `INVESTIGATOR` if the UI ever needs accurate org charts vs trial PI lists (currently trial PIs live only in case study text).

---

## Recommendations — data completeness (next ingest passes)

1. Add **Precision Supplements** and **VRx My·Biotics** product entities if downstream work needs supplement-level linking.
2. Add remaining **named executives** (and optionally advisory board) as `Person` rows with `executives.connect` where verified.
3. When ClinicalTrials.gov posts **results** for NCT05465616, NCT06174428, etc., update `outcomeSummary` / `fullTextSummary` or add a dedicated results snippet field per schema design.
4. Reconcile **episode number** vs **URL** in the podcast pipeline so public `1228` and DB `episodeNumber` are consistent if that matters for search.
5. Optional: attach Viome as **`sponsorOrganizations`** on the episode if editorially confirmed (paid sponsor vs guest appearance).

---

## File purpose

This report documents the GraphQL ingestion performed for MISSION-003 for audit, future schema work, and handoff to the next research or engineering pass.
