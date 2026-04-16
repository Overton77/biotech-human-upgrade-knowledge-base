---
type: research
title: "Viome evidence map"
created: 2026-04-15
updated: 2026-04-15
mission: MISSION-003-viome-deep-dive
episode: "1228"
episode_id: "692b888d004e71ed86aa236c"
tags: [research, viome, evidence, trials, pubmed, diagnostics]
confidence: high
---

# Viome Evidence Map

## Evidence Hierarchy

- `Company-asserted`: product pages, company pages, CancerDetect marketing pages, research blog
- `Peer-reviewed`: PubMed-indexed methods, oral-health, and diagnostic papers
- `Registry`: ClinicalTrials.gov sponsor records
- `Independent`: press coverage and product reviews, useful for context but not efficacy
- `Financial filing`: none confirmed in this mission

## Key Peer-Reviewed Papers

| Evidence object | What it supports | Evidence type | Assessment |
|---|---|---|---|
| `PMID 32772558` blood transcriptome test | viability of small-volume capillary blood transcriptomics for systems-biology workflows | peer-reviewed methods / validation | `Supported` for platform logistics; not direct clinical utility proof |
| `PMID 36622006` saliva metatranscriptomic test | viability of ambient-temperature saliva metatranscriptomics | peer-reviewed methods / validation | `Supported` for sample collection and workflow claims |
| `PMID 37454545` oral / throat cancer signature | CancerDetect / CDOT diagnostic performance in high-risk cohort | peer-reviewed diagnostic validation | `Preliminary-to-supported`; company-linked but directly relevant |
| `PMID 38328005` saliva pathway scores | oral pathway scores for precision-wellness framing | peer-reviewed association study | `Preliminary`; useful for oral-score plausibility, not direct clinical utility |
| `PMID 38319053` subgingival proxy method | oral microbiome sampling methodology | peer-reviewed methods | `Supported` for sampling-method innovation |
| `PMID 40128554` synthetic control samples | CLIA-lab diagnostic QC / reproducibility support | peer-reviewed methods | `Supported` for test-operations infrastructure |

## Key Registry Records

| NCT ID | Program | Design signal | Assessment |
|---|---|---|---|
| `NCT05451303` | OralViome Cancer Testing System | observational, `n=475`, recruiting | strong registry support for active cancer-testing program |
| `NCT06174428` | Validity of Viome's Oral/throat Cancer Test | observational, `n=1000`, recruiting | strong current registry support for sensitivity / specificity validation |
| `NCT05972330` | VRx MyBiotics Oral Lozenges | completed interventional study, `n=34` | useful but small and company-sponsored |
| `NCT05465616` | Precision Nutrition Program for HbA1c | randomized placebo-controlled, recruiting, `n=150` | important clinical-utility lane, still pending completion |

## Claim Cluster Assessment

### 1. RNA / metatranscriptomic testing platform

- Strongest support comes from `PMID 32772558` and `PMID 36622006`.
- These papers support the feasibility and workflow robustness of blood and saliva transcriptomic / metatranscriptomic testing.
- They do **not** by themselves prove that every consumer score or recommendation has clinical utility.

Assessment: `Supported` for platform methodology, `Preliminary` for broad clinical-outcome implications.

### 2. Oral-health scoring and oral microbiome insights

- `PMID 38328005` supports the idea that oral functional pathways can associate with oral / oropharyngeal disease phenotypes.
- `PMID 38319053` strengthens the oral-sampling methods story.
- Current consumer oral-health claims still outrun the independent evidence ceiling for many everyday user-facing benefits.

Assessment: `Preliminary`.

### 3. CancerDetect / oral-throat cancer detection

- Website claims: specificity `95%`, OSCC sensitivity `90%`, OPSCC sensitivity `90%` on current product pages.
- `PMID 37454545` reports specificity `94%`, OSCC sensitivity `90%`, and OPSCC sensitivity `84.2%` in the independent validation cohort described in the paper.
- Current registry records `NCT05451303` and `NCT06174428` show the program is active and still being validated.

Assessment: `Preliminary-to-supported` for use as a promising diagnostic aid in high-risk populations; not established as a routine population-screening standard.

### 4. Precision nutrition and downstream supplements

- Registry evidence exists for HbA1c / diabetes and several broader precision-nutrition programs.
- However, many consumer claims still depend on ongoing studies, company summaries, or company-generated recommendation logic.

Assessment: `Preliminary`.

## Main Caveats

- Many pivotal studies are company-linked or company-sponsored.
- Consumer pages blend validated laboratory workflow claims with broader health-improvement promises.
- The strongest evidence is around sample-processing methods and oral-cancer diagnostic development, not around every downstream personalized product claim.

## Related Notes

- [[publications-and-trials-source]]
- [[cancerdetect-oral-throat]]
- [[viome-life-sciences]]
- [[product-catalog]]

## Sources

- [[publications-and-trials-source]]
- PubMed: `32772558`, `36622006`, `37454545`, `38328005`, `38319053`, `40128554`
- ClinicalTrials.gov: `NCT05451303`, `NCT06174428`, `NCT05972330`, `NCT05465616`
