---
type: synthesis
title: "Qualia company and product slice synthesis"
created: 2026-04-15
updated: 2026-04-15
mission: MISSION-004-qualia-deep-dive
episode: "1296"
episode_id: "692b8834004e71ed86aa1e6c"
tags: [synthesis, qualia, products, ingredients, rebrand]
confidence: medium
---

# Qualia company and product slice synthesis

## Bottom line

This mission slice established a strong current-state foundation for `Qualia Life Sciences` as an active supplement company with a materially broader current catalog than the seed alone implied. The company / brand relationship with `Neurohacker Collective` is now clearer at the public-site level, the current product lane is substantially stronger, and a second round materially improved ingestion readiness by building out product, compound, people, and study entities.

## What this slice completed

- Bootstrapped `MISSION-004-qualia-deep-dive` in the vault.
- Confirmed `tvly` availability and authenticated state using the vault API key.
- Captured current official company, rebrand, people, and FAQ pages.
- Built a current product inventory from official menu and live product pages.
- Extracted targeted ingredient and pricing chunks for flagship products.
- Added mission-scoped organization, person, product, and branded-ingredient notes for the most important currently surfaced joint-health lane.
- Expanded the mission-scoped entity layer to cover the active current catalog, mission-scoped compound rows, additional science-team people, and official study pages from the current studies hub.

## Key findings

- Current official footer and product pages use `Qualia Life Sciences, LLC`.
- Official 2024 rebrand content says `Neurohacker Collective` became `Qualia Life Sciences`, but the exact registry-grade legal transition still needs verification.
- Current active public product menu includes at least:
  - `Qualia Mind`
  - `Qualia Mind Caffeine Free`
  - `Qualia Mitochondria+`
  - `Qualia NAD+`
  - `Qualia Senolytic`
  - `Qualia Joint Health`
  - `Qualia Stem Cell`
  - `Qualia Creatine+`
  - `Qualia Magnesium+`
  - `Qualia Night`
  - `Qualia Probiotic+`
- `Qualia Joint Health` is the clearest current evidence-lane anchor because its ingredient page explicitly ties dose choices to named branded ingredients and study logic.
- `Qualia NAD+` is a second strong evidence-lane anchor because the current official page and ingredient page explicitly foreground the `67%` NAD+ claim, `3` NAD precursors, and `NIAGEN`.
- The mission now has `11` product notes, `150` compound notes, `9` people notes, and `19` study notes inside `04-entities`, making the folder substantially more useful for downstream ingestion.

## Main cautions

- A clean public filing or business-registry chain for the `Neurohacker Collective` to `Qualia Life Sciences, LLC` transition was not completed in this slice.
- Browser validation began hitting Cloudflare rate limiting after the core catalog was captured.
- Exact one-time pricing remains incomplete for several products even though active status and ingredient architecture were established.
- This slice still prioritizes current catalog and entity completeness over full PubMed / trial verification.
- One current `Mitochondria+` ingredient row was partially corrupted in rendered DOM text around `ProcynCi`, so that exact row text should be rechecked before any label-perfect ingestion.

## Unresolved Questions

- What is the exact registry-grade legal relationship between `Neurohacker Collective`, any older operating entities, and `Qualia Life Sciences, LLC`?
- What are the exact current one-time prices and package details for `Mind`, `Mind Caffeine Free`, `Creatine+`, `Stem Cell`, and `Probiotic+` after Cloudflare cools down?
- Which product claims are supported by exact whole-product trials versus only ingredient-level or branded-ingredient studies?
- How strong and independent is the evidence behind `Joint Health`, `Senolytic`, and `NAD+` once sponsorship and replication are checked systematically?

## Next Steps / Recommendations

- [high] Run the next mission slice on product-claim evidence, starting with [[qualia-joint-health]], [[ovomet]], [[tamaflex]], and [[apresflex]].
- [high] Run a dedicated `Qualia NAD+` evidence pass, including `NIAGEN`, the claimed `67%` NAD+ increase, and commercial sponsorship review.
- [medium] Return for a second live browser pass on the remaining products after Cloudflare rate limits reset.
- [medium] Resolve the exact entity and legal-name chain through business-registry or filing-grade lookup before making stronger ownership or legal-history claims.

## Created / Updated File Paths

- `missions/MISSION-004-qualia-deep-dive/00-inbox/MISSION-004-qualia-deep-dive.md`
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
