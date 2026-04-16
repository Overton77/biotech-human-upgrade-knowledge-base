---
type: mission
status: active
created: 2026-04-15
updated: 2026-04-15
episode: "1296"
episode_id: "692b8834004e71ed86aa1e6c"
guest_speaker_full_name: "Gregory Kelly"
timeframe: "current / recent through 2026-04-15"
confidence: medium
tags: [mission, qualia, neurohacker, supplements, ingredients, longevity, research]
---

# MISSION-004: Qualia Deep Dive

## Objective

Build a current-state research package on Qualia as an organization and product ecosystem, with emphasis on current product catalog, formulation and ingredient completeness, branded ingredient sourcing, and whether key marketing claims are supported by traceable human evidence.

## Starter Material

- **Episode guest (full name):** Gregory Kelly — Chief Product Officer, Qualia Life Sciences (from seed `curated_content/human_upgrade/episode-entities-pre-research/episode-692b8834004e71ed86aa1e6c.md`; listed as Dr. Gregory Kelly in the seed).
- Episode URL: `https://daveasprey.com/1296-qualia-greg-kelly/`
- Starter seed: `curated_content/human_upgrade/episode-entities-pre-research/episode-692b8834004e71ed86aa1e6c.md`
- Vault root: `human_upgrade_research/human-upgrade-biotech-research/`
- Timeframe: `current / recent through 2026-04-15`

## Scope

- Current company fundamentals and brand/entity structure
- Current product catalog and active commercial architecture
- Ingredient-complete product capture where publicly available
- Pricing, subscription structure, serving size, dosage, and caution language
- Branded ingredients and important reused compounds
- Current public science, evidence, and study support for core claims
- Business, filing, or controversy context when materially relevant

## Out Of Scope

- Exhaustive historical product catalog unless it materially informs the current state
- Non-Qualia brands except where they clarify current Qualia or Neurohacker entity structure
- Deep ingredient science for every minor supporting ingredient in the first pass

## Key Entities To Track

### Organizations

- Qualia Life Sciences
- Qualia
- Neurohacker or Neurohacker Collective related entities where currently relevant
- Branded ingredient suppliers that materially recur across products

### People

- Greg Kelly
- Current executives, founders, and science/product leadership surfaced during research

### Products / Services

- Qualia Joint Health
- Qualia Senolytic
- Qualia NAD+
- Qualia Mitochondria+
- Qualia Mind and other current flagship products surfaced during catalog work

### Compounds / Branded Ingredients

- Ovomet
- TamaFlex
- ApresFlex
- L-carnitine
- Other high-salience compounds and branded ingredients reused across current products

## Evidence Lanes

1. Company fundamentals and site mapping
2. Product catalog and ingredient capture
3. Branded ingredient and compound inventory
4. Product-claim evidence and cited studies
5. Mission synthesis

## Lane Assignment

This mission instance is focused first on:

1. Mission bootstrap and vault setup
2. Tavily-backed domain and product discovery
3. Ingredient-complete product capture for current Qualia supplement pages
4. Current company/entity context needed to interpret the product stack

## Deliverables

- Mission note updates in `00-inbox/`
- Raw captures in `01-sources/raw-json/`
- Readable source notes in `01-sources/markdown/`
- Working analysis in `02-research/`
- Entity notes in `04-entities/`
- Synthesis note in `03-syntheses/`

## Status Log

| Date | Action |
|------|--------|
| 2026-04-15 | Mission created from the Qualia staged prompt and episode seed. |
| 2026-04-15 | Required biotech, vault, Tavily, and browser skills reviewed. |
| 2026-04-15 | Tavily CLI checked, confirmed available, and authenticated with the vault API key. |
| 2026-04-15 | Mission container scaffolded under `missions/MISSION-004-qualia-deep-dive/`. |
| 2026-04-15 | Tavily discovery and extraction completed for official company pages, people pages, product pages, and ingredient pages. |
| 2026-04-15 | Live browser validation captured current purchase options for `Qualia Joint Health`, `Qualia NAD+`, `Qualia Mitochondria+`, and `Qualia Magnesium+`; later follow-up hit Cloudflare rate limiting. |
| 2026-04-15 | Source notes, a product matrix, an organization note, a person note, a flagship product note, branded-ingredient notes, and a mission slice synthesis were added. |
| 2026-04-15 | A second research round expanded the entity layer to cover the active current product catalog, mission-scoped compound notes, additional people notes, and official study / case-study notes. |

## Current Findings

- Current official pages support `Qualia Life Sciences, LLC` as the active public company identity, with the `Neurohacker Collective` relationship clarified at the public rebrand-story level but not yet registry-verified.
- Current active public product pages include `Qualia Mind`, `Qualia Mind Caffeine Free`, `Qualia Mitochondria+`, `Qualia NAD+`, `Qualia Senolytic`, `Qualia Joint Health`, `Qualia Stem Cell`, `Qualia Creatine+`, `Qualia Magnesium+`, `Qualia Night`, and `Qualia Probiotic+`.
- `Qualia Joint Health` is currently the strongest ingredient-evidence anchor in the mission because its page exposes a complete branded-ingredient table and explicit dose logic for `Ovomet`, `TamaFlex`, and `ApresFlex`.
- `Qualia NAD+`, `Qualia Mitochondria+`, and `Qualia Magnesium+` have strong current-state pricing and purchase-option validation from live rendered pages.
- The entity layer is materially stronger after the second round, now covering `11` current products, `150` mission-scoped compound rows, `9` people, and `19` official study or case-study notes.
- Most current product formulas are now represented in product notes with label-level ingredient tables suitable for downstream ingestion, with the main remaining caveat being one partially corrupted `Mitochondria+` row around `ProcynCi`.

## Unresolved Questions

- What is the exact registry-grade legal relationship between `Neurohacker Collective` and `Qualia Life Sciences, LLC`?
- What are the exact current one-time prices and package details for `Mind`, `Mind Caffeine Free`, `Creatine+`, `Stem Cell`, and `Probiotic+` once rate limits reset?
- Which company-cited studies support exact whole-product claims versus only ingredient-level or mechanistic support?
- How strong and independent is the evidence behind `Joint Health`, `Senolytic`, and `NAD+` after sponsorship and replication checks?

## Next Steps / Recommendations

- [high] Run the next evidence slice on `Qualia Joint Health`, beginning with `Ovomet`, `TamaFlex`, and `ApresFlex`.
- [high] Run a dedicated evidence slice on `Qualia NAD+`, including `NIAGEN`, the `67%` NAD+ claim, and commercial-sponsorship mapping.
- [medium] Return for a second live product-page pass after Cloudflare rate limits cool down to finish exact pricing and package details for the remaining products.
- [medium] Resolve the `Neurohacker Collective` to `Qualia Life Sciences, LLC` entity chain through business-registry or filing-grade lookup.

## Created / Updated Paths

- `missions/MISSION-004-qualia-deep-dive/00-inbox/MISSION-004-qualia-deep-dive.md`
- `missions/MISSION-004-qualia-deep-dive/01-sources/raw-json/2026-04-15-qualia-domain-map.json`
- `missions/MISSION-004-qualia-deep-dive/01-sources/raw-json/2026-04-15-qualia-company-context-search.json`
- `missions/MISSION-004-qualia-deep-dive/01-sources/raw-json/2026-04-15-qualia-business-filings-search.json`
- `missions/MISSION-004-qualia-deep-dive/01-sources/raw-json/2026-04-15-qualia-product-discovery-search.json`
- `missions/MISSION-004-qualia-deep-dive/01-sources/raw-json/2026-04-15-qualia-formulation-discovery-search.json`
- `missions/MISSION-004-qualia-deep-dive/01-sources/raw-json/2026-04-15-qualia-official-people-search.json`
- `missions/MISSION-004-qualia-deep-dive/01-sources/raw-json/2026-04-15-qualia-senolytic-search.json`
- `missions/MISSION-004-qualia-deep-dive/01-sources/raw-json/2026-04-15-qualia-mitochondria-search.json`
- `missions/MISSION-004-qualia-deep-dive/01-sources/raw-json/2026-04-15-qualia-additional-products-search.json`
- `missions/MISSION-004-qualia-deep-dive/01-sources/raw-json/2026-04-15-qualia-official-pages-extract.json`
- `missions/MISSION-004-qualia-deep-dive/01-sources/raw-json/2026-04-15-qualia-product-pages-extract.json`
- `missions/MISSION-004-qualia-deep-dive/01-sources/raw-json/2026-04-15-qualia-product-detail-chunks.json`
- `missions/MISSION-004-qualia-deep-dive/01-sources/raw-json/2026-04-15-qualia-ingredient-detail-chunks.json`
- `missions/MISSION-004-qualia-deep-dive/01-sources/raw-json/2026-04-15-qualia-remaining-product-detail-chunks.json`
- `missions/MISSION-004-qualia-deep-dive/01-sources/markdown/2026-04-15-qualia-company-and-web-footprint.md`
- `missions/MISSION-004-qualia-deep-dive/01-sources/markdown/2026-04-15-qualia-current-product-catalog.md`
- `missions/MISSION-004-qualia-deep-dive/02-research/products/qualia-current-product-and-ingredient-matrix.md`
- `missions/MISSION-004-qualia-deep-dive/02-research/products/qualia-entity-ingestion-coverage.md`
- `missions/MISSION-004-qualia-deep-dive/03-syntheses/qualia-company-and-product-slice-synthesis.md`
- `missions/MISSION-004-qualia-deep-dive/04-entities/organizations/qualia-life-sciences.md`
- `missions/MISSION-004-qualia-deep-dive/04-entities/people/`
- `missions/MISSION-004-qualia-deep-dive/04-entities/products/`
- `missions/MISSION-004-qualia-deep-dive/04-entities/compounds/`
- `missions/MISSION-004-qualia-deep-dive/04-entities/studies/`
