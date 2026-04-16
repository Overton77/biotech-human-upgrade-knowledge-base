---
type: synthesis
title: "TruDiagnostic mission synthesis"
created: 2026-04-15
updated: 2026-04-15
mission: MISSION-006-trudiagnostic-deep-dive
episode: "883"
episode_id: "692b8877004e71ed86aa2216"
tags: [synthesis, trudiagnostic, diagnostics, epigenetics, evidence]
confidence: medium
---

# TruDiagnostic mission synthesis

## Bottom line

TruDiagnostic currently presents as a Lexington, Kentucky-based epigenetic diagnostics company operating across consumer testing, provider-facing diagnostics, research services, and intervention-linked study work. The strongest current evidence supports the existence of a real commercial platform built around `TruAge`, `TruHealth`, `OMICmAge`, `DunedinPACE`, and an organ-systems-age layer aligned with `SYMPHONYAge`, but the public product surface still blends direct analytes, methylation-derived proxies, published clock families, and marketing-heavy risk outputs in ways that require careful separation.

## Company and business context

- Official pages, the shop contact surface, and the rules page place the company at `881 Corporate Dr, Lexington, KY 40503`.
- The official rules page identifies the sponsor as `TruDiagnostic, Inc.`
- A Kentucky court document separately uses the variant `Tru Diagnostics, Inc.`, so exact legal-name normalization still deserves registry-grade follow-up.
- No clean SEC or Form D trail was confirmed in this mission.
- The company has a meaningful research-commercialization posture:
  - NIH SBIR claim for the W-Function Epigenomic Roadmap
  - research-service pages with arrays, WGBS, bioinformatics, and multi-omic language
  - multiple sponsor-linked ClinicalTrials.gov records

## Product and service architecture

### Consumer products

- [[trudiagnostic-truage]]
- [[trudiagnostic-truhealth]]
- [[trudiagnostic-truage-truhealth]]

### Embedded clock and report layers

- [[trudiagnostic-omicmage]]
- [[trudiagnostic-dunedinpace-reporting]]
- [[trudiagnostic-symphonyage]]

### Research-service line

- [[trudiagnostic-research-services]]

### Practical product takeaways

- Current public shop prices are strongest for consumer products:
  - TruAge: `$499`
  - TruHealth: `$499`
  - TruAge + TruHealth: `$849`
- Public turnaround language ranges from `2-3 weeks` to `3-4 weeks`, with older FAQ-style `4-6 weeks` wording still visible on support surfaces.
- The sample report and support-center content materially improve the public biomarker surface, especially for TruAge.
- `TruAge` versus `TruAge COMPLETE` remains partially conflated in the public stack.

## Biomarkers and report outputs

The mission now has a much better public inventory of:

- direct analytes such as CRP, IL-6, HgbA1c, glucose, ApoB, LDL-C, HDL-C, triglycerides, NAD+, PFAS, creatinine, and many vitamin or amino-acid markers
- methylation clock outputs such as OMICmAge, DunedinPACE, SYMPHONYAge, FitAge, telomere length, and immune-cell deconvolution
- risk-style outputs such as mortality risk, type 2 diabetes risk, cancer risk, smoking impact, alcohol impact, and weight-loss response
- organ-system lists and sample-report biomarker examples from the public PDF

Still, the exact public boundary between directly measured values and methylation-derived proxies remains incomplete for the full TruHealth stack.

## Evidence assessment

### Strongest independent evidence

- [[pmid-35029144-dunedinpace]] provides the cleanest independent support for the DunedinPACE algorithm family.
- [[pmid-40954326-systems-age]] provides the strongest peer-reviewed organ-systems-age paper currently aligned with the `SYMPHONYAge` concept.

### Strongest company-linked publication layer

- [[pmid-41741793-omicmage]] is the strongest current OMICmAge paper and includes a TruDiagnostic validation cohort and affiliation.
- [[pmid-38455390-methylationepic-v2]] supports platform and assay-context claims around EPIC v2 usage.
- [[pmid-41746138-senolytic-nonreversal]] is especially important as a limitation paper because it pushes back against simplistic intervention-reversal narratives.

### Registry evidence

The ClinicalTrials.gov search surfaced a meaningful sponsor-linked study set, including:

- [[nct05294835-ketamine-and-epigenetic-aging]]
- [[nct04962464-fast-diet-and-calorie-mimetic]]
- [[nct05001646-emf-protection-device]]
- [[nct04988542-sleep-supplement]]

This is strong evidence that TruDiagnostic uses epigenetic-age endpoints across real registered intervention studies. It is not, by itself, proof of positive results or clinical utility.

## Main cautions

- Public product counts and feature lists are internally inconsistent.
- The company mixes direct analytes, inferred methylation proxies, and broad interpretation layers under the same commercial umbrellas.
- Registry records show study intent, but many do not yet have an obvious linked results publication.
- `SYMPHONYAge` is commercially clear but still requires caution when mapping the brand directly onto the independent `Systems Age` paper.

## Work completed

- Completed Stage 1 company fundamentals and business-context work.
- Built a current product and service catalog.
- Built a consolidated biomarker and report inventory.
- Added a support-center and sample-report gap-fill source set.
- Added a product matrix research note.
- Added a research-publications and validation hub.
- Built a mission evidence map.
- Created mission-scoped product notes and study notes.
- Updated the organization note with stronger legal-name evidence.

## Key findings

- TruDiagnostic now has a solid mission-scoped evidence base for company structure, products, biomarker surface, and research posture.
- Public pricing and sample-report assets are available without login for the main consumer products.
- The company has both company-linked publications and independently anchored algorithm literature.
- The company also has a substantial sponsor-linked ClinicalTrials.gov footprint.
- The biggest remaining limitations are packaging ambiguity, incomplete proxy-versus-direct-measure distinction, and unresolved filing-grade business history.

## Unresolved Questions

- What is the best registry-grade normalization of `TruDiagnostic, Inc.` versus `Tru Diagnostics, Inc.`?
- Which of the TruDiagnostic-sponsored NCT studies now have results or downstream publications?
- What is the exact current product difference between `TruAge` and `TruAge COMPLETE`?
- Which TruHealth outputs are directly measured and which are inferred from methylation-based epigenetic biomarker proxies?
- Is there a stronger public document that maps the branded `SYMPHONYAge` commercial product directly to a specific published methodology?

## Next Steps / Recommendations

- [high] Follow the sponsor-linked NCT set for posted results, publications, or preprints and add them to the study layer as they appear.
- [high] Resolve the legal-name variant through a Kentucky business-registry lookup if filing-grade precision is required for downstream ingestion.
- [medium] If a future mission needs higher-fidelity biomarker completeness, capture the non-public TruHealth sample report or provider-facing report views.
- [medium] Split direct analytes from proxy-derived outputs more rigorously before any structured ingestion.
- [medium] Track whether the current `TruAge` shop product is effectively the same as `TruAge COMPLETE` or only the current commercial successor.

## Created / Updated File Paths

- `missions/MISSION-006-trudiagnostic-deep-dive/01-sources/markdown/product-and-service-catalog.md`
- `missions/MISSION-006-trudiagnostic-deep-dive/01-sources/markdown/biomarker-and-report-inventory.md`
- `missions/MISSION-006-trudiagnostic-deep-dive/01-sources/markdown/research-publications-and-validation-hub.md`
- `missions/MISSION-006-trudiagnostic-deep-dive/01-sources/markdown/support-center-and-sample-report.md`
- `missions/MISSION-006-trudiagnostic-deep-dive/02-research/products/trudiagnostic-product-and-report-matrix.md`
- `missions/MISSION-006-trudiagnostic-deep-dive/02-research/validation/trudiagnostic-evidence-map.md`
- `missions/MISSION-006-trudiagnostic-deep-dive/03-syntheses/trudiagnostic-mission-synthesis.md`
- `missions/MISSION-006-trudiagnostic-deep-dive/04-entities/products/trudiagnostic-truage.md`
- `missions/MISSION-006-trudiagnostic-deep-dive/04-entities/products/trudiagnostic-truage-complete.md`
- `missions/MISSION-006-trudiagnostic-deep-dive/04-entities/products/trudiagnostic-truhealth.md`
- `missions/MISSION-006-trudiagnostic-deep-dive/04-entities/products/trudiagnostic-truage-truhealth.md`
- `missions/MISSION-006-trudiagnostic-deep-dive/04-entities/products/trudiagnostic-omicmage.md`
- `missions/MISSION-006-trudiagnostic-deep-dive/04-entities/products/trudiagnostic-symphonyage.md`
- `missions/MISSION-006-trudiagnostic-deep-dive/04-entities/products/trudiagnostic-dunedinpace-reporting.md`
- `missions/MISSION-006-trudiagnostic-deep-dive/04-entities/products/trudiagnostic-research-services.md`
- `missions/MISSION-006-trudiagnostic-deep-dive/04-entities/studies/pmid-41741793-omicmage.md`
- `missions/MISSION-006-trudiagnostic-deep-dive/04-entities/studies/pmid-35029144-dunedinpace.md`
- `missions/MISSION-006-trudiagnostic-deep-dive/04-entities/studies/pmid-40954326-systems-age.md`
- `missions/MISSION-006-trudiagnostic-deep-dive/04-entities/studies/pmid-41746138-senolytic-nonreversal.md`
- `missions/MISSION-006-trudiagnostic-deep-dive/04-entities/studies/pmid-38455390-methylationepic-v2.md`
- `missions/MISSION-006-trudiagnostic-deep-dive/04-entities/studies/nct05294835-ketamine-and-epigenetic-aging.md`
- `missions/MISSION-006-trudiagnostic-deep-dive/04-entities/studies/nct04962464-fast-diet-and-calorie-mimetic.md`
- `missions/MISSION-006-trudiagnostic-deep-dive/04-entities/studies/nct05001646-emf-protection-device.md`
- `missions/MISSION-006-trudiagnostic-deep-dive/04-entities/studies/nct04988542-sleep-supplement.md`
