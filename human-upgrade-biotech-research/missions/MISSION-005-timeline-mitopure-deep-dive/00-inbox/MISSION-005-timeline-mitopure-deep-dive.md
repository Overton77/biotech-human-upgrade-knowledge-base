---
type: mission
status: complete
created: 2026-04-15
updated: 2026-04-15
episode: "1225"
episode_id: "692b888d004e71ed86aa2369"
guest_speaker_full_name: "Anurag Singh"
timeframe: "current / recent through 2026-04-15"
confidence: medium
tags: [mission, timeline, amazentis, mitopure, urolithin-a, longevity, research]
---

# MISSION-005: Timeline / Mitopure Deep Dive

## Objective

Build a current-state research package on Timeline, Amazentis, Mitopure, and Urolithin A, covering company fundamentals, product catalog, ingredient and formulation details, commercialization structure, and the clinical evidence used to support mitochondrial, muscle, immune, and skin-aging claims.

## Starter Material

- **Episode guest (full name):** Anurag Singh — Chief Medical Officer, Timeline (Amazentis); credentials in seed: M.D., Ph.D. (from `curated_content/human_upgrade/episode-entities-pre-research/episode-692b888d004e71ed86aa2369.md`).
- Episode URL: `https://daveasprey.com/1225-timeline-anurag-singh/`
- Starter seed: `curated_content/human_upgrade/episode-entities-pre-research/episode-692b888d004e71ed86aa2369.md`
- Vault root: `human_upgrade_research/human-upgrade-biotech-research/`
- Timeframe: `current / recent through 2026-04-15`

## Scope

- Current relationship between Timeline, Timeline Nutrition, Amazentis, and Mitopure
- Leadership, scientific leadership, partnerships, commercialization structure, and business context
- Core domains, key site sections, and official science or product pages
- Current product and bundle inventory
- Ingredient, excipient, and specification capture for current products wherever publicly visible
- Urolithin A and Mitopure identity, framing, delivery formats, and proprietary positioning
- Human evidence, trial registrations, sponsorship links, and marketing-claim support

## Out Of Scope

- Exhaustive historical chronology unless it materially changes current-state interpretation
- Broad general longevity coverage unrelated to Timeline, Amazentis, Mitopure, or Urolithin A
- Deep mechanistic speculation unsupported by traceable literature or registry evidence

## Key Entities To Track

### Organizations

- Timeline
- Timeline Nutrition
- Amazentis
- Nestle Health Science
- Other strategic partners surfaced during research

### People

- Anurag Singh
- Current executives, founders, and scientific leadership surfaced during research

### Products / Technologies

- Mitopure softgels or capsules
- Mitopure powders, protein, or shake products
- Mitopure skin or topical products
- Urolithin A
- Mitopure as both branded ingredient and product system

## Evidence Lanes

1. Company fundamentals, web footprint, and business context
2. Product catalog and ingredient capture
3. Compound identity and technology framing
4. Evidence map, trials, and sponsorship links
5. Mission synthesis and cleanup

## Lane Assignment

This mission instance is being executed in the following order:

1. Mission bootstrap and Tavily readiness
2. Company fundamentals and domain mapping
3. Product inventory and specification capture
4. Evidence and trial validation
5. Final synthesis and entity cleanup

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
| 2026-04-15 | Mission created from the Timeline / Anurag Singh episode seed and staged prompt. |
| 2026-04-15 | Required mission, vault, Tavily, and browser skills reviewed. |
| 2026-04-15 | Tavily CLI verified as authenticated and ready for use. |
| 2026-04-15 | Mission container scaffolded under `missions/MISSION-005-timeline-mitopure-deep-dive/`. |
| 2026-04-15 | Stage 1 completed: official company pages, Timeline / Amazentis relationship signals, leadership, and financing context captured. |
| 2026-04-15 | Stage 2 completed: current oral catalog and skincare catalog captured, including browser-verified pricing and oral ingredient panels. |
| 2026-04-15 | Stage 3 completed: key human-study anchors, registry links, and Urolithin A identity notes captured with PMID / DOI / NCT provenance where available. |
| 2026-04-15 | Stage 4 completed: source notes, research notes, entity notes, and a mission synthesis were added; mission marked complete. |

## Current Findings

- Timeline currently presents as the consumer-facing brand while first-party materials still describe `Amazentis` as the parent company behind Mitopure.
- The active oral catalog is currently concentrated around three delivery formats of the same core active dose: gummies, softgels, and powder, each priced at `$99` one-time with lower subscription tiers.
- The active skincare catalog currently includes at least six Mitopure-branded products, with the strongest captured detail on the firming serum.
- The oral product pages currently expose full ingredient panels in text, which materially improves catalog quality and reduces dependence on image-only supplement facts.
- The strongest human evidence anchors in this mission are PMIDs `32694802`, `35050355`, `35584623`, and `41174221`.
- Timeline's evidence base is materially stronger than average supplement-brand evidence, but much of the highest-value literature remains commercially linked to Amazentis / Timeline authors or collaborators.

## Unresolved Questions

- What is the exact current legal and commercial relationship between Timeline and Amazentis?
- What is the exact legal-entity stack connecting `Timeline`, `Timeline Longevity`, and `Amazentis SA`?
- Which newly registered Mitopure trials now have posted final results or downstream publications?
- Has the topical skin-aging preprint advanced to a peer-reviewed final paper?
- What are the full INCI ingredient lists for the non-serum skincare products currently active in the catalog?

## Next Steps / Recommendations

- [high] Resolve the exact legal-entity structure through Swiss and U.S. registry-grade sources if filing precision is needed.
- [high] Track newer registry records such as `NCT07231783` and `NCT07231848` for publications, result postings, or commercial-formulation implications.
- [medium] Capture full INCI ingredient lists for the remaining skincare line before the catalog changes.
- [medium] Separate generic Urolithin A evidence from Mitopure-specific evidence before any downstream ingestion or ontology work.
- [medium] Revisit the skin-evidence lane once the topical preprint reaches peer review or additional clinical publications appear.

## Created / Updated Paths

- `missions/MISSION-005-timeline-mitopure-deep-dive/00-inbox/MISSION-005-timeline-mitopure-deep-dive.md`
- `missions/MISSION-005-timeline-mitopure-deep-dive/01-sources/raw-json/2026-04-15-timeline-domain-map.json`
- `missions/MISSION-005-timeline-mitopure-deep-dive/01-sources/raw-json/2026-04-15-amazentis-domain-map.json`
- `missions/MISSION-005-timeline-mitopure-deep-dive/01-sources/raw-json/2026-04-15-timeline-company-context-search.json`
- `missions/MISSION-005-timeline-mitopure-deep-dive/01-sources/raw-json/2026-04-15-timeline-root-and-studies-extract.json`
- `missions/MISSION-005-timeline-mitopure-deep-dive/01-sources/raw-json/2026-04-15-timeline-core-product-pages-extract.json`
- `missions/MISSION-005-timeline-mitopure-deep-dive/01-sources/raw-json/2026-04-15-timeline-about-and-financing-extract.json`
- `missions/MISSION-005-timeline-mitopure-deep-dive/01-sources/raw-json/2026-04-15-urolithin-a-muscle-study-search.json`
- `missions/MISSION-005-timeline-mitopure-deep-dive/01-sources/raw-json/2026-04-15-urolithin-a-first-human-study-search.json`
- `missions/MISSION-005-timeline-mitopure-deep-dive/01-sources/raw-json/2026-04-15-urolithin-a-middle-aged-study-search.json`
- `missions/MISSION-005-timeline-mitopure-deep-dive/01-sources/raw-json/2026-04-15-urolithin-a-immune-study-search.json`
- `missions/MISSION-005-timeline-mitopure-deep-dive/01-sources/raw-json/2026-04-15-urolithin-a-immune-paper-search.json`
- `missions/MISSION-005-timeline-mitopure-deep-dive/01-sources/raw-json/2026-04-15-urolithin-a-trial-registry-search.json`
- `missions/MISSION-005-timeline-mitopure-deep-dive/01-sources/raw-json/2026-04-15-urolithin-a-pubchem-search.json`
- `missions/MISSION-005-timeline-mitopure-deep-dive/01-sources/markdown/2026-04-15-timeline-web-footprint.md`
- `missions/MISSION-005-timeline-mitopure-deep-dive/01-sources/markdown/product-and-skincare-catalog.md`
- `missions/MISSION-005-timeline-mitopure-deep-dive/01-sources/markdown/publications-and-trials-source.md`
- `missions/MISSION-005-timeline-mitopure-deep-dive/02-research/company-fundamentals/timeline-company-fundamentals-and-business-context.md`
- `missions/MISSION-005-timeline-mitopure-deep-dive/02-research/products/timeline-product-and-skincare-matrix.md`
- `missions/MISSION-005-timeline-mitopure-deep-dive/02-research/evidence/timeline-mitopure-evidence-map.md`
- `missions/MISSION-005-timeline-mitopure-deep-dive/03-syntheses/timeline-mission-synthesis.md`
- `missions/MISSION-005-timeline-mitopure-deep-dive/04-entities/organizations/timeline-amazentis.md`
- `missions/MISSION-005-timeline-mitopure-deep-dive/04-entities/people/anurag-singh.md`
- `missions/MISSION-005-timeline-mitopure-deep-dive/04-entities/products/timeline-mitopure-gummies.md`
- `missions/MISSION-005-timeline-mitopure-deep-dive/04-entities/products/timeline-mitopure-softgels.md`
- `missions/MISSION-005-timeline-mitopure-deep-dive/04-entities/products/timeline-mitopure-powder.md`
- `missions/MISSION-005-timeline-mitopure-deep-dive/04-entities/products/timeline-mitopure-firming-serum.md`
- `missions/MISSION-005-timeline-mitopure-deep-dive/04-entities/compounds/urolithin-a.md`
- `missions/MISSION-005-timeline-mitopure-deep-dive/04-entities/studies/pmid-32694802-urolithin-a-first-human.md`
- `missions/MISSION-005-timeline-mitopure-deep-dive/04-entities/studies/pmid-35050355-urolithin-a-older-adults.md`
- `missions/MISSION-005-timeline-mitopure-deep-dive/04-entities/studies/pmid-35584623-urolithin-a-middle-aged-adults.md`
- `missions/MISSION-005-timeline-mitopure-deep-dive/04-entities/studies/pmid-41174221-urolithin-a-immune-aging.md`
