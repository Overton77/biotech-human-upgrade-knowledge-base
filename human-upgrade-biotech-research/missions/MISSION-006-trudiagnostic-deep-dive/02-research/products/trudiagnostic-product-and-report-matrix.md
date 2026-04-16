---
type: research
title: "TruDiagnostic product and report matrix"
created: 2026-04-15
updated: 2026-04-15
mission: MISSION-006-trudiagnostic-deep-dive
episode: "883"
episode_id: "692b8877004e71ed86aa2216"
tags: [research, trudiagnostic, products, reports, biomarkers]
confidence: medium
---

# TruDiagnostic product and report matrix

## Analytical framing

TruDiagnostic’s public product architecture appears to have three overlapping layers:

1. consumer kits sold through the shop
2. provider-facing ordering and portal workflows
3. research and service infrastructure built around methylation arrays, sequencing, and bioinformatics

The company mixes direct analyte-style reporting, inferred methylation-risk scores, organ-age clocks, and lifestyle-risk outputs in the same public marketing surface. Stage 3 must keep these categories separate.

## Product matrix

| Offering | Public category | Intended user | Specimen | Core measurement framing | Main outputs | Price visibility | Key uncertainties |
|------|------|------|------|------|------|------|------|
| TruAge | Consumer longevity test | Consumer | Finger-prick blood | `1 million+` CpG sites, aging algorithms | OMICmAge, DunedinPACE, SYMPHONYAge, telomere, fitness, immune, inflammation, risk-style outputs | Public | Whether all outputs belong to standard TruAge or only TruAge COMPLETE |
| TruHealth | Consumer systems-health test | Consumer | Finger-prick blood | Epigenetic methylation-derived biomarker and systems-health reporting | Nutrients, fats, amino acids, inflammation, neurocognitive, toxins, oxidative stress, mitochondria, NAD, ketones | Public | Exact final biomarker count and which listed items are directly measured vs inferred |
| TruAge + TruHealth | Consumer bundle | Consumer | Finger-prick blood | Combined longevity plus systems-health reporting | Union of TruAge and TruHealth outputs | Public | Whether the public `180+` total is current and stable |
| TruAge provider program | Provider-ordered test | Provider / clinic | Blood spot card or lavender-top EDTA | Same core epigenetic-test framing with provider workflow | TruAge family reports plus provider support | Gated | Wholesale pricing, report differentiation by provider tier |
| TruHealth provider program | Provider-ordered test | Provider / clinic | Blood spot card or lavender-top EDTA | Same epigenetic systems-health framing | TruHealth family reports | Gated | Wholesale pricing and whether provider version exposes the same report surface |
| PgX | Provider add-on | Provider / clinic | Not clearly stated | Pharmacogenetic testing | 140+ drugs across classes | Gated | Specimen, assay platform, and evidence layer |
| EPISEEK | Provider add-on | Provider / clinic | ctDNA | Multi-cancer detection from epigenomic modifications | Abnormal signal or no-signal cancer report | Gated | Specific validation set and clinical status |
| Research services | Research / B2B | Academic, clinical, industry | Blood, saliva, tissue | Array sequencing, EPIC v2, custom arrays, WGBS, genotyping, bioinformatics | Data generation, multi-omic integration, manuscript support, methylation risk scoring | Mostly gated | Exact deliverables, pricing structure, API or data-access details |

## Measurement categories to preserve

### Directly named analytes or lab-style metrics

- Vitamins, amino acids, fatty-acid categories, ApoB, LDL-C, HDL-C, triglycerides, HgbA1c, glucose, CRP, IL-6, white blood cell count, neutrophils, lymphocytes, PFAS, acrolein, myeloperoxidase, NAD+, 1-MNA, beta-hydroxybutyrate, alpha-ketoglutarate, spermidine

### Inferred composite or category outputs

- Nutrient & Vitamin Levels
- Metabolic Health
- Energy Levels
- Neurocognitive Markers
- Toxin Exposure Levels
- Heavy Metal Exposure Levels
- Oxidative Defense
- Mitochondrial Function
- Gut-Brain Health Marker

### Methylation clocks and organ-age models

- OMICmAge
- DunedinPACE
- SYMPHONYAge
- FitAge / Fitness Age
- Telomere Length report

### Risk-style or interpretation outputs

- Mortality Risk
- Type 2 Diabetes Risk
- Cancer Risk
- Smoking Impact Score
- Alcohol Impact Score
- Weight Loss Response

## Most important Stage 3 caution

The public product surface combines:

- directly named biomarker-style outputs
- inferred methylation risk scores
- published clock families
- company-specific report packaging

These should not be treated as a single evidence class.

## Public inconsistencies

| Topic | Public mismatch |
|------|------|
| TruHealth biomarker count | `105+`, `110+`, and in some contexts `150+` |
| TruAge turnaround | `2-3 weeks`, `3-4 weeks`, and `4-6 weeks` in older FAQ content |
| TruAge naming | `TruAge`, `TruAge COMPLETE`, and `TruAge PACE` appear across older and newer surfaces |
| OMICmAge naming | `OMICmAge` and `OMICAge` both appear |
| company scale | `15,000+` tested vs `100,000+` tested across different pages |

## Highest-value unresolved questions

- Which outputs are specific to `TruAge COMPLETE` versus baseline `TruAge` today?
- Which TruHealth outputs are direct measurements versus methylation-derived proxies?
- Are `Fitness Age`, `FitAge`, and `grip strength / gait speed` separate report layers or alternate public labels for the same model family?
- Which of the reported risk outputs have peer-reviewed validation specific to the current commercial implementation?

## Related Notes

- [[product-and-service-catalog]]
- [[biomarker-and-report-inventory]]
- [[trudiagnostic]]

## Sources

- [TruAge](https://trudiagnostic.com/truage)
- [TruHealth](https://www.trudiagnostic.com/truhealth)
- [Providers](https://trudiagnostic.com/providers)
- [About tests](https://trudiagnostic.com/about-tests)
- [Our Services](https://trudiagnostic.com/our-services)
- [TruAge + TruHealth shop page](https://shop.trudiagnostic.com/products/truage-truhealth)
- [TruHealth shop page](https://shop.trudiagnostic.com/products/truhealth)
- [TruAge FAQ](https://shop.trudiagnostic.com/pages/truage-faq)
