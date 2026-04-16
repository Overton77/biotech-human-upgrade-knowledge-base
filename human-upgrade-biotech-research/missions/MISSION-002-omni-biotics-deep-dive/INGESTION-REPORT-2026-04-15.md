# MISSION-002 GraphQL ingestion report

**Date:** 2026-04-15  
**Mission:** `MISSION-002-omni-biotics-deep-dive`  
**Episode resolved by:** `episodePageUrl` = `https://daveasprey.com/1387-omni-biotics/`  
**Database episode:** `id` `cmo0kczq009nhu8o2fq8t7df7`, slug `human-upgrade-1387`, `episodeNumber` **1387**

Sources: `04-entities/` organization, person, product, compound, and study notes; `03-syntheses/omni-biotics-synthesis.md`; `01-sources/markdown/company-foundations.md`; episode pre-research `curated_content/human_upgrade/episode-entities-pre-research/episode-69d2b7a91d80f4e37ec4545e.md` for canonical URL and guest bio context.

---

## Created / updated (humanupgrade-graphql)

### Organizations

| Action | slug | Notes |
|--------|------|--------|
| Create | `institut-allergosan-holding-gmbh` | `HOLDING_COMPANY`; Austrian holding layer; domains `allergosan.com` |
| Create | `institut-allergosan` | `MANUFACTURER`; Institut AllergoSan Pharma GmbH; Graz; founded 1991 |
| Create | `allergo-san-usa` | `BRAND`; U.S. retail layer; `omnibioticlife.com`; launched 2019 |
| Update | `institut-allergosan` | `owners` → Anita Frauwallner; `executives` → Bernd Assinger |
| Update | `allergo-san-usa` | `executives` → Klaus, Hannah, Lena Kleinfeld |

### People

| Action | slug |
|--------|------|
| Create | `anita-frauwallner`, `hannah-kleinfeld`, `klaus-kleinfeld`, `lena-kleinfeld`, `bernd-assinger` |

### Compounds (strains)

| Action | slug |
|--------|------|
| Create | `bifidobacterium-bifidum-w23`, `bifidobacterium-lactis-w51`, `lactobacillus-salivarius-w24`, `lactococcus-lactis-w58` |

### Products (all `organizationId` → AllergoSan USA)

| Action | slug |
|--------|------|
| Create | `omni-biotic-stress-release`, `omni-biotic-ab-10`, `omni-biotic-balance`, `omni-biotic-hetox`, `omni-biotic-panda`, `omni-biotic-power`, `caricol`, `caricol-gastro`, `omni-logic-plus`, `omni-logic-immune` |

### Product ↔ compounds (`containsCompounds`)

- **Stress Release:** W23, W51, W24  
- **AB 10:** W24, W51, W23  
- **Balance:** W58  
- **Hetox:** W23, W24, W58, W51  
- **Panda:** W58, W51, W23  
- **Power:** W58, W23, W51  
- Prebiotics and Caricol SKUs: no compound links (not live-culture products in this ontology)

### Case studies

Created 11 rows with PubMed/DOI/registry-linked `fullTextSummary` where applicable; `referencedByOrganizations` → `institut-allergosan` + `allergo-san-usa` (company-cited / portfolio-relevant literature; no `businessSponsors` set—independent academic publications referenced by brand materials).

| slug |
|------|
| `bagga-2018-emotional-brain-signatures` |
| `bagga-2019-resting-state-connectivity` |
| `moser-2019-ibsd-synbiotic` |
| `leblhuber-2018-alzheimers-dementia` |
| `horvath-2020-diabesity-synbiotic` |
| `sabico-2017-t2dm-endotoxin` |
| `strasser-2016-power-athletes-urti` |
| `niers-2009-panda-eczema` |
| `muss-2013-caricol-digestive-disorders` |
| `weiser-2018-caricol-gastro-gastritis` |
| `lang-2010-ab10-aad` |

### Episode

| Action | detail |
|--------|--------|
| Update | `updateEpisode` where `episodePageUrl` = mission URL → `guests.connect` → `hannah-kleinfeld` |

Embedding: all create/update mutations used `embedding: { mode: AUTO }` where supported.

---

## Intentional gaps / follow-ups

1. **Mission YAML vs DB:** Episode metadata in mission YAML aligns with DB (`1387`, `human-upgrade-1387`).  
2. **Products listed in mission but not in `04-entities`:** Stress Release Kids, AB 10 Kids, Cat & Dog, Gut Health Reset Program, Dynamic Probiotic Duo, Immune Support Bundle—no durable entity notes; not ingested. Add product notes then re-ingest if needed.  
3. **U.S. scientific advisory board** (named on company site): no person entities in vault—skipped.  
4. **Holding ↔ operating legal edges:** No parent-org FK in schema from this ingest; relationship described in org `description` fields only.  
5. **`businessSponsors`:** Left empty; trials are primarily published academic work cited by the brands—use `businessSponsors` later if sponsor-run trials are explicitly curated.  
6. **Lab tests / biomarkers:** Not applicable to this mission (no lab panel entities in vault).  
7. **Caricol case studies:** `CreateCaseStudy` left `doi` null where vault had no DOI; PubMed `sourceUrl` present.

---

## Schema / data follow-ups

- Consider editorial pass on **episode** `publishStatus` / `isPublished` when content is ready for public catalog.  
- Optional: add **DOI** on Muss/Weiser case study rows if sourced later.  
- **Lang 2010** remains lower-evidence-tier vs PubMed-flagship rows—already flagged in `fullTextSummary`.
