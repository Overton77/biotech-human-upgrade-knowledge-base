---
type: synthesis
title: "STEMREGEN / Kalyagen — Research Synthesis"
tags: [synthesis, stemregen, kalyagen, stem-cells, evidence-assessment]
created: 2026-04-07
updated: 2026-04-07
confidence: high
---

# STEMREGEN / Kalyagen — Research Synthesis

## Executive Summary

**STEMREGEN** is a direct-to-consumer supplement brand (legal entity: Biomics LLC, DBA Kalyagen) founded in 2016 by [[christian-drapeau|Christian Drapeau]], a neurophysiology MSc from McGill who has spent ~20 years developing botanical stem cell mobilizer supplements. The company sells a three-product protocol (Release, Signal, Mobilize) positioned around **endogenous stem cell mobilization (ESCM)** — the idea that plant-derived compounds can release bone marrow stem cells into circulation to support tissue repair.

The company has experienced significant commercial growth (Inc. 5000 in 2024 and 2025, 297% 3-year revenue growth) and has built a substantial presence in the biohacking/longevity community through podcast appearances, conference sponsorships, and influencer partnerships.

## The Evidence Picture

### What Is Supported

1. **The basic biology is real.** Stem cell mobilization from bone marrow is established science. The CXCL12/CXCR4 axis, selectins, and integrins control HSC retention. Pharmacologic agents (G-CSF, plerixafor) can powerfully mobilize stem cells.

2. **Some botanical compounds can modestly increase circulating CD34+ cells.** Small crossover trials (n=12) show ~18–33% increases in various stem cell subpopulations after single doses of AFA extract or sea buckthorn extract. One partial independent replication exists (Merino et al., Madrid, 2020).

3. **Several compounds in the formulas have legitimate independent pharmacology.** Curcumin, astaxanthin, NAC, nattokinase, pterostilbene, and hydroxytyrosol are well-studied compounds with established anti-inflammatory, antioxidant, or circulatory benefits.

### What Is Not Supported

1. **No clinical outcome trial of any finished STEMREGEN product exists.** The evidence base consists of small pilot studies of individual ingredients, not the retail products.

2. **The "10 million additional stem cells" marketing claim is not independently verified.** It derives from company-affiliated research using surrogate biomarkers.

3. **The mobilization-to-repair logical chain is broken.** Even G-CSF (50–100× more powerful than any botanical) has failed to consistently improve tissue repair outcomes in clinical trials for MI, stroke, and PVD. An 18–25% increase from a supplement is implausible to produce clinical repair through the same mechanism.

4. **The oral bioavailability gap is critical.** Key compounds (fucoidan, beta-glucan, ginsenosides) have strong parenteral evidence but poor oral absorption. The studies showing mobilization used injectable or in vitro preparations, not oral supplements.

5. **No study tests the three-product protocol (Release + Signal + Mobilize) together.** The synergy claim is entirely theoretical.

### Conflicts of Interest

The evidence base has a **circular structure**:
- [[christian-drapeau|Christian Drapeau]] formulates the products
- [[gitte-jensen|Gitte Jensen's]] NIS Labs (a contract research org) tests them
- Drapeau publishes the results
- The results are used to market the products
- No independent group has replicated the key findings with the same formulations

This is common in the supplement industry but represents a significant structural limitation on evidence quality.

## Corporate History Context

The STEMREGEN story cannot be fully understood without its MLM origins:

1. Drapeau co-founded **STEMTech International** (~2005) as an MLM company selling StemEnhance
2. STEMTech filed **Chapter 11 bankruptcy** (2017) after Drapeau's departure
3. STEMTech **sued Drapeau** (2016) for trade secret misappropriation — court denied the claim
4. STEMTech products had a **Prop 65 lead contamination settlement** (2015)
5. STEMREGEN/Kalyagen was founded in 2016 with a **D2C + affiliate model** (not MLM)

The shift from MLM to D2C represents a meaningful business model improvement, but the scientific evidence base carried over from the STEMTech era remains the foundation.

## Evidence Quality Matrix

| Claim | Evidence Level | Independent Replication | Clinical Outcomes |
|-------|---------------|----------------------|-------------------|
| AFA increases circulating CD34+ | Low (n=12 pilot) | Partial (Merino 2020) | None |
| SBB-PE increases circulating stem cells | Low (n=12 pilot) | None | None |
| StemAloe increases stem cells by 80% | Very low (predatory journal) | None | None |
| Release product mobilizes stem cells | None (no product-level trial) | N/A | None |
| Signal reduces inflammatory noise | Plausible (individual ingredients) | N/A | None |
| Mobilize improves microcirculation | Plausible (individual ingredients) | N/A | None |
| Protocol improves health outcomes | None | N/A | None |
| CHF trial shows benefit | Company-asserted (not published) | N/A | Unverifiable |

## Comparison to Pharmacologic Standard

| Feature | G-CSF (Gold Standard) | STEMREGEN Release |
|---------|----------------------|-------------------|
| Mobilization magnitude | 50–100× increase | ~18–33% increase (individual ingredients) |
| Evidence base | Thousands of patients, FDA-approved | n=12 pilots, commercially-affiliated |
| Clinical outcomes | Mixed (fails in MI/stroke trials) | None tested |
| Route | Subcutaneous injection | Oral supplement |
| Regulatory status | FDA-approved drug | Dietary supplement (not FDA-evaluated) |

## Unresolved Questions

1. What is the actual dose of each ingredient in the proprietary blends?
2. Has the finished Release product ever been tested in a human study? (Only one rat study exists: PMID 39907413)
3. What happened to the CHF and Parkinson's trials mentioned on the website?
4. Is chronic daily stem cell mobilization safe long-term?
5. What is the actual corporate relationship between Kalyagen and the Spanish trial sponsors?
6. What are the company's actual revenue figures?

## Recommended Next Actions

- [ ] Monitor for publication of CHF trial results
- [ ] Search for NCT05699694 (Parkinson's trial) updates
- [ ] Attempt to verify revenue through Inc. 5000 data or other sources
- [ ] Track any new peer-reviewed publications from Drapeau/Jensen
- [ ] Monitor FDA enforcement actions in the stem cell supplement space
- [ ] Research competitor products making similar ESCM claims

## Database Ingestion Readiness

The following entities are ready for GraphQL ingestion:

| Entity Type | Slug | Ready? |
|------------|------|--------|
| Person | christian-drapeau | Yes |
| Person | gitte-jensen | Yes |
| Organization | stemregen-kalyagen | Yes |
| Organization | stemtech-international | Yes |
| Product | stemregen-release | Yes |
| Product | stemregen-sport | Yes |
| Product | stemregen-signal | Yes |
| Product | stemregen-mobilize | Yes |
| CaseStudy | sbb-pe-rct-pmid-30787601 | Yes |
| CaseStudy | nct04515537-afa-svf-hf | Yes |

See [[graphql-ingestion-stemregen|GraphQL Ingestion Data]] for structured payloads.

## Related Notes

- [[christian-drapeau|Christian Drapeau]]
- [[stemregen-kalyagen|STEMREGEN / Kalyagen]]
- [[stemtech-international|STEMTech International]]
- [[gitte-jensen|Gitte Jensen]]
- [[stemregen-release|STEMREGEN Release]]
- [[stemregen-signal|STEMREGEN Signal]]
- [[stemregen-mobilize|STEMREGEN Mobilize]]
- [[stemregen-sport|STEMREGEN Release SPORT]]
- [[sbb-pe-rct-pmid-30787601|SBB-PE RCT Study]]
- [[nct04515537-afa-svf-hf|NCT04515537 Heart Failure Trial]]
- [[escm-science-review|ESCM Science Review]]
- [[compound-analysis|Compound Analysis]]
