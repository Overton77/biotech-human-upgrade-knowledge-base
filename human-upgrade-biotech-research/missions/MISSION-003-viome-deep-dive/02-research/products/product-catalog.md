---
type: research
title: "Viome product catalog and technology inventory"
created: 2026-04-15
updated: 2026-04-15
mission: MISSION-003-viome-deep-dive
episode: "1228"
episode_id: "692b888d004e71ed86aa236c"
tags: [research, viome, products, diagnostics, metatranscriptomics]
confidence: high
---

# Viome Product Catalog And Technology Inventory

## Current Catalog Shape

Viome's current public offering is best understood as a stack:

1. At-home tests that measure microbial and / or human gene-expression signals
2. Personalized recommendations delivered through the app
3. Personalized downstream products such as supplements, gut biotics, and oral-care formulas
4. A separate oral / throat cancer diagnostic-aid product with provider review

## Consumer Test Inventory

| Product | Intended user | Sample type | Outputs | Price captured | Turnaround / logistics |
|---|---|---|---|---:|---|
| [[full-body-intelligence]] | user wanting broad whole-body / longevity framing | stool, saliva, finger-prick blood | `50+` to `60+` health scores, BioAge, inflammation, food recommendations, app access | `$399` | `2-3 weeks`, CLIA-lab shipment |
| [[gut-intelligence]] | gut-health focused user | stool | `20+` health scores, `370+` food recommendations, gut recommendations | `$279` | `2-3 weeks`, CLIA-lab shipment |
| [[oral-health-intelligence]] | oral-health focused user | saliva | `16` oral scores, oral microbiome / gum / cavity metrics, food recommendations | `$259` | timing not clearly surfaced in focused extract |
| [[cancerdetect-oral-throat]] | adult at elevated oral / throat cancer risk | saliva | qualitative cancer-associated molecular-feature detection with provider follow-up | `from $599` | eligibility review plus result in `~4 weeks` |

## Technology / Measurement Model

### Directly stated by Viome

- RNA-based testing rather than static DNA analysis
- gut microbial gene expression for Gut Intelligence
- saliva-based oral microbiome and pathway scoring for Oral Health Intelligence
- combined microbiome and cellular-function framing for Full Body Intelligence
- saliva human + microbial metatranscriptomic features for CancerDetect

### Current public outputs

- food recommendations
- health scores
- BioAge and inflammation framing on Full Body Intelligence
- oral-health scores on Oral Health Intelligence
- personalized formulation recommendations for supplements, gut biotics, toothpaste / gel, and oral lozenges

## Personalized Product Inventory

| Product / line | Publicly named composition | Notes |
|---|---|---|
| Precision Supplements | vitamins, minerals, herbs, enzymes, amino acids, botanicals; `50+` possible personalized ingredients | exact formula individualized |
| VRx My·Biotics Gut Formula | example strains / ingredients include `Bacillus clausii CSI08`, `Bifidobacterium breve Bb-03`, `Partially Hydrolyzed Guar Gum` | positioned as personalized probiotic + prebiotic blend |
| VRx My·Biotics Oral Lozenges | minimum `30 billion` beneficial oral biotics; example strains include `Streptococcus salivarius`, `S. salivarius M18`, `Lactobacillus acidophilus`, `Ligilactobacillus salivarius`, `KT-11` | oral prebiotic / probiotic / postbiotic support |
| VRx My·Biotics Toothpaste & Gel | oral-biotic personalization plus evidence-backed actives; named gel actives include `MSM` and `STPP` | day / night oral-care system framing |

## Biomarker / Metric Visibility Assessment

### Publicly visible

- score counts and score families
- broad domains such as oral pathogen activity, cavity-promoting microbes, inflammatory activity, metabolic fitness, gut lining strength, BioAge, inflammation, and cardiovascular / immune / brain / heart health framing
- saliva or stool or blood sample modality

### Not fully public

- complete biomarker list for most consumer tests
- exact formulas for personalized downstream products
- full mapping from each score to every underlying analyte or molecular feature

### Completeness judgment

`Partial`.

Viome publicly exposes product architecture, score families, and some example pathways / organisms, but not a full analyte-by-analyte or score-by-score biomarker inventory across the whole consumer stack. This mission surfaced enough to characterize the platform, but not to claim a complete biomarker list.

## Key Product Observations

- The strongest commercially differentiated layer is not just "microbiome testing" but the closed loop from testing to personalized intervention.
- Oral health is strategically important: it appears both as a standalone test line and as a bridge into CancerDetect.
- Full Body Intelligence appears to be Viome's flagship broad-consumer product, while Gut Intelligence remains the foundational entry test.
- CancerDetect is more tightly regulated in its copy than the wellness products, with explicit safety language and provider-review steps.

## Related Notes

- [[product-catalog-source]]
- [[full-body-intelligence]]
- [[gut-intelligence]]
- [[oral-health-intelligence]]
- [[cancerdetect-oral-throat]]

## Sources

- [[product-catalog-source]]
- `missions/MISSION-003-viome-deep-dive/01-sources/raw-json/viome-test-focused.json`
- `missions/MISSION-003-viome-deep-dive/01-sources/raw-json/viome-personalized-products-focused.json`
