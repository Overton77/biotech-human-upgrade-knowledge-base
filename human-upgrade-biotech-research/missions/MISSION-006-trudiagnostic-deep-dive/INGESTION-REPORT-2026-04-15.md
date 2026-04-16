# MISSION-006 GraphQL ingestion report — 2026-04-15

## Scope

Ingestion for **TruDiagnostic** (MISSION-006-trudiagnostic-deep-dive) into the Human Upgrade GraphQL database via MCP `humanupgrade-graphql`: organization, guest person, products, lab tests with biomarker wiring, case studies with sponsor/reference links, and episode guest attachment by **`episodePageUrl`**.

**Episode URL used (canonical):** `https://daveasprey.com/ryan-smith-trudiagnostic-883/`

**Note:** The database episode resolved by this URL currently has slug `human-upgrade-919`, title “Human Upgrade Episode 919”, and `episodeNumber` 919. The mission YAML lists `episode: "883"`; only **`guests.connect`** was applied so as not to rewrite episode metadata or trigger unnecessary embedding churn.

## Created / updated entities

### Organization

- **Created:** `Organization` **slug `trudiagnostic`** (`LAB`), legal name **TruDiagnostic, Inc.**, headquarters **881 Corporate Dr, Lexington, KY 40503**, website `https://trudiagnostic.com/`, domains `trudiagnostic.com`, `shop.trudiagnostic.com`, aliases including **Tru Diagnostics, Inc.**, long-form description from vault company fundamentals.

### Person

- **Created:** **slug `ryan-smith`**, title and bio aligned with `04-entities/people/ryan-smith.md`, LinkedIn URL set.

### Organization ↔ person

- **Updated:** `trudiagnostic` **`owners`** and **`executives`** → **connect** `ryan-smith`.

### Products (8)

All linked with **`organizationId`** to `trudiagnostic`:

| Slug | Notes |
|------|--------|
| `trudiagnostic-truage` | $499, panel definition, TruAge URLs |
| `trudiagnostic-truage-complete` | $499, shop “complete” packaging |
| `trudiagnostic-truhealth` | $499, systems-health panel |
| `trudiagnostic-truage-truhealth` | $849 bundle |
| `trudiagnostic-omicmage` | $15 upgrade signal |
| `trudiagnostic-symphonyage` | Organ-system report layer |
| `trudiagnostic-dunedinpace-reporting` | DunedinPACE reporting |
| `trudiagnostic-research-services` | Research / turnkey services |

**Skipped:** `containsCompounds` — no mission-grade compound ontology beyond general supplement mentions.

### Lab tests (3)

| Slug | Product link | Role |
|------|----------------|------|
| `trudiagnostic-lab-test-truage` | TruAge product | Epigenetic aging panel + sample-PDF anchor |
| `trudiagnostic-lab-test-truhealth` | TruHealth product | Systems-health biomarker panel |
| `trudiagnostic-lab-test-truage-truhealth` | Bundle product | Combined panel |

- **TruAge biomarkers:** ~**59** rows — clocks (OMICmAge, DunedinPACE), **11 SYMPHONYAge** organ scores, risk/lifestyle/immunity/fitness outputs, and **sample Advanced TruAge PDF** analytes from `biomarker-and-report-inventory.md`.
- **TruHealth biomarkers:** ~**103** rows — vitamins, amino acids, antioxidants, lipids/apolipoproteins, glycemic, immune/inflammatory, neurocognitive labels, gut, toxins, NAD/ketone/mitochondrial markers per vault inventory.
- **Bundle lab test:** **`connect`** to existing biomarker slugs so the combined test references the **union** of TruAge + TruHealth markers without duplicating create payloads.

### Case studies (9)

**ClinicalTrials.gov (sponsor = TruDiagnostic)** — **`businessSponsors`** → `trudiagnostic`:

- `nct05294835-ketamine-and-epigenetic-aging`
- `nct04962464-fast-diet-and-calorie-mimetic`
- `nct05001646-emf-protection-device`
- `nct04988542-sleep-supplement`

**Peer-reviewed, company-affiliated (per mission notes)** — **`businessSponsors`** → `trudiagnostic`:

- `pmid-41741793-omicmage` (DOI 10.1038/s43587-026-01073-7)
- `pmid-41746138-senolytic-nonreversal` (DOI 10.1111/acel.70430)
- `pmid-38455390-methylationepic-v2` (DOI 10.1186/s43682-023-00021-5)

**Independent publications referenced by the company’s product story** — **`referencedByOrganizations`** → `trudiagnostic`:

- `pmid-35029144-dunedinpace` (DunedinPACE foundation paper)
- `pmid-40954326-systems-age` (Systems Age / organ systems — conceptual parallel to SYMPHONYAge)

Each row includes **`sourceUrl`**, **`doi`** where applicable, and non-stub **`description`**, **`fullTextSummary`**, **`outcomeSummary`**.

### Episode

- **Updated:** episode where **`episodePageUrl`** = `https://daveasprey.com/ryan-smith-trudiagnostic-883/` → **`guests.connect`** **`ryan-smith`**, **`embedding`:** `{ "mode": "AUTO" }`.

## Sources used (vault)

- `00-inbox/MISSION-006-trudiagnostic-deep-dive.md`
- `04-entities/organizations/trudiagnostic.md`, `people/ryan-smith.md`, `products/*`, `studies/*`
- `01-sources/markdown/biomarker-and-report-inventory.md`, `product-and-service-catalog.md`
- `03-syntheses/trudiagnostic-mission-synthesis.md`

## Gaps / follow-ups

1. **Episode numbering:** DB episode number/title vs mission YAML “883” — confirm editorial source of truth; guest link is correct via URL.
2. **Legal name:** Kentucky registry check for **TruDiagnostic, Inc.** vs **Tru Diagnostics, Inc.** (vault flags variant).
3. **TruAge vs TruAge COMPLETE:** Product differentiation remains partially conflated in public materials; DB has both products with honest caveats.
4. **Biomarker completeness:** TruHealth public counts (105+ vs 150+) are inconsistent; not every marketing-listed analyte has a separate row — expand if provider-only or portal-only lists are captured later.
5. **Measured vs methylation-proxy:** Schema stores report-layer biomarkers; explicit “direct assay vs inferred” flags are not in the ingested payload (would need schema/product conventions).
6. **NCT outcomes:** Registry studies ingested as evidence of **intent**; link results publications when available.

## Embedding / search

- All create/update mutations that support **`embedding`** used **`{ "mode": "AUTO" }`** (or equivalent omit) per ingestion skill.
- Avoided touching episode scalar fields beyond **`guests`** to reduce no-op search-field rewrites.
