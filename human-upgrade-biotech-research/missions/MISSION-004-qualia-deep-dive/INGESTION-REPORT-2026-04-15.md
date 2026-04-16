# Ingestion report — MISSION-004 Qualia Deep Dive

**Date:** 2026-04-15  
**GraphQL:** `humanupgrade-graphql` MCP (`Create*` / `Update*` with `embedding: { mode: AUTO }` where applicable)  
**Mission root:** `human_upgrade_research/human-upgrade-biotech-research/missions/MISSION-004-qualia-deep-dive/`

## Resolved episode

- **episodePageUrl:** `https://daveasprey.com/1296-qualia-greg-kelly/`
- **Note:** The database row uses internal `slug` `human-upgrade-1328` and `episodeNumber` **1328** while the canonical web URL path is **1296**. Ingestion used `episodePageUrl` as the unique key per skill; **aligning title/slug/episode number with episode 1296** is a recommended editorial/data follow-up (no scalar episode fields were changed in this ingest).

## Created / updated

### Organization (1)

| Action   | Slug                 | Id                       |
|----------|----------------------|--------------------------|
| Created | `qualia-life-sciences` | `cmo0pk38l003k20o2ys397use` |

- **Type:** `BRAND`  
- **Fields:** `legalName`, `description`, `websiteUrl`, `domains`, `headquarters`, `tags`, `aliases`  
- **Relations:** `owners.connect` → `james-schmachtenberger`; `executives.connect` → `greg-kelly`, `dan-pardi`, `shawn-ramer`, `daniel-stickler`, `heather-sandison`, `colin-gardner`, `sarah-blomquist`, `sara-adaes`

### People (9 created)

| Slug                  | Full name               |
|-----------------------|-------------------------|
| `greg-kelly`          | Gregory Kelly           |
| `james-schmachtenberger` | James Schmachtenberger |
| `dan-pardi`           | Dan Pardi               |
| `shawn-ramer`         | Shawn Ramer             |
| `daniel-stickler`     | Daniel Stickler         |
| `heather-sandison`    | Heather Sandison        |
| `colin-gardner`       | Colin Gardner           |
| `sarah-blomquist`     | Sarah Blomquist         |
| `sara-adaes`          | Sara Adaes              |

Bios, titles, URLs, and expertise areas follow `04-entities/people/` and the organization note.

### Products (11 created)

All linked with `organizationId` → Qualia Life Sciences.

| Slug                     | Name                          | Price (USD) where set |
|--------------------------|-------------------------------|------------------------|
| `qualia-joint-health`    | Qualia Joint Health           | 79                     |
| `qualia-mind-2-0`        | Qualia Mind 2.0               | 159                    |
| `qualia-mind-caffeine-free` | Qualia Mind Caffeine Free  | —                      |
| `qualia-mitochondria-plus` | Qualia Mitochondria+       | 179                    |
| `qualia-nad-plus`        | Qualia NAD+                 | 79                     |
| `qualia-senolytic`       | Qualia Senolytic             | —                      |
| `qualia-stem-cell`       | Qualia Stem Cell             | —                      |
| `qualia-creatine-plus`   | Qualia Creatine+             | —                      |
| `qualia-magnesium-plus`  | Qualia Magnesium+            | 49                     |
| `qualia-night`           | Qualia Night                 | 79                     |
| `qualia-probiotic-plus`  | Qualia Probiotic+            | —                      |

Each record includes `productUrl`, `description`, `recommendedUse` (where the vault had dosing/pricing context), `categories`, `benefits`, and `tags` from `04-entities/products/`.

### Case studies (19 created, then sponsor-linked)

All slugs match `04-entities/studies/*.md` frontmatter. Each received `UpdateCaseStudy` → `businessSponsors.connect` → `qualia-life-sciences` (company-hosted or company-run study pages; none were classified as independent third-party citations requiring `referencedByOrganizations` only).

Slugs:  
`qualia-joint-health-beta-study`, `nad-clinical2`, `qualia-senolytic-placebo-controlled-clinical-study-results`, `qualia-nad-placebo-controlled-clinical-study`, `how-personalized-lifestyle-interventions-are-making-a-meaningful-impact-on-cognitive-decline`, `repultable-health-qualia-night-study`, `qualia-senolytic-studyrand-sf-36`, `qualia-nad-beta-study`, `qualia-synbiotic-pilot-study`, `qualia-life-pilot-study`, `qualia-life-agemeter-pilot-study`, `qualia-life-survey-results-1`, `qualia-senolytic-pilot-study-1`, `qualia-magnesium-pre-launch-beta-study-results`, `qualia-mind-prelaunch-beta-study`, `qualia-probiotic-beta-study`, `qualia-stem-cell-beta-study`, `qualia-stem-cell-proteomics-pilot-study`, `qualia-creatine-pilot-study`

### Episode

- **Update:** `updateEpisode` where `episodePageUrl` = mission URL → `guests.connect` → `greg-kelly`

### Media (2026-04-15 follow-up — Tavily + `createMedia`)

Public image URLs were discovered with the **Tavily** MCP (`tavily_search` with `include_images`, and `tavily_extract` with `include_images` on `qualialife.com` / `cdn1.neurohacker.com`). Each asset was attached with **`createMedia`** (parent `organizationId`, `productId`, or `personId`).

| Parent | Count | Notes |
|--------|-------|--------|
| **Organization** `qualia-life-sciences` | 2 | Wordmark logo + homepage hero webp |
| **Products** | 3 | `qualia-joint-health`, `qualia-mind-2-0`, `qualia-nad-plus` — official product imagery from shop pages |
| **People** | 6 | `greg-kelly`, `james-schmachtenberger`, `shawn-ramer`, `daniel-stickler`, `heather-sandison`, `sarah-blomquist` |

**Not attached (this pass):** `dan-pardi`, `colin-gardner`, `sara-adaes` — no unambiguous dedicated portrait URL on the Qualia CDN from extraction; safe to add later when a stable headshot URL is confirmed.

## Intentionally not ingested (scope / schema)

- **`containsCompounds` on products:** Mission vault lists ~150 compound notes; the skill asks to skip empty ontology and only wire compounds when there is a clear DB mapping strategy. Ingredient-level compound graphing is a follow-on batch (resolve existing `Compound` slugs vs create, then `updateProduct.containsCompounds`).
- **Lab tests / biomarkers:** No `04-entities` lab-test panel definitions; products are dietary supplements, not diagnostic panels. **`isLabTestPanelDefinition`** left default (false).
- **Separate “Neurohacker Collective” organization:** Captured as **alias** on Qualia Life Sciences; no second org row without registry-grade confirmation.

## Sources used

- `00-inbox/MISSION-004-qualia-deep-dive.md` (episode URL, guest name, scope)
- `04-entities/organizations/qualia-life-sciences.md`
- `04-entities/people/*.md` (9)
- `04-entities/products/*.md` (11)
- `04-entities/studies/*.md` (19)
- Cross-checks from `03-syntheses/qualia-company-and-product-slice-synthesis.md` and `02-research/products/` where needed for wording

## Gaps and follow-ups

1. **Episode numbering:** Reconcile DB `episodeNumber` / `slug` with public **1296** URL (data quality).
2. **Clinical evidence:** Pull DOIs / PubMed IDs for `nad-clinical2` and other trials into `doi` / `fullTextSummary` when peer-reviewed versions exist.
3. **Pricing:** Backfill missing USD list prices for Mind Caffeine Free, Senolytic, Stem Cell, Creatine+, Probiotic+ after live page refresh (Cloudflare limits noted in mission log).
4. **Compounds:** Optional second-pass `updateProduct` with `containsCompounds` for flagship formulas (e.g. Joint Health branded actives) once compound entities exist or are created with stable slugs.
5. **Registry verification:** Legal relationship Neurohacker Collective ↔ Qualia Life Sciences, LLC (mission open question).
