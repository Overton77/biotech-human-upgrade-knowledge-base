---
type: research
title: "GraphQL Ingestion Data — STEMREGEN Mission"
tags: [ingestion, graphql, database, stemregen]
created: 2026-04-07
updated: 2026-04-07
---

# GraphQL Ingestion Data — STEMREGEN Mission

Structured data ready for ingestion via the `humanupgrade-graphql` MCP server.

## Persons

### Christian Drapeau

```json
{
  "slug": "christian-drapeau",
  "fullName": "Christian Drapeau",
  "firstName": "Christian",
  "lastName": "Drapeau",
  "title": "Founder & Chief Science Officer, STEMREGEN",
  "bio": "Stem cell scientist (MSc Neurophysiology, McGill), author of Cracking the Stem Cell Code, founder and CSO of STEMREGEN/Kalyagen. Pioneered the concept of Endogenous Stem Cell Mobilization (ESCM). 9+ US patents on botanical stem cell mobilizers. Previously co-founded STEMTech International.",
  "websiteUrl": "https://www.stemregen.co/pages/about",
  "linkedinUrl": "https://www.linkedin.com/in/christian-drapeau",
  "xUrl": "https://www.instagram.com/stemcellchristian/",
  "aliases": ["C. Drapeau", "stemcellchristian"],
  "expertiseAreas": ["stem cell mobilization", "neurophysiology", "cyanobacteria", "nutraceuticals", "endogenous stem cell mobilization"]
}
```

### Gitte S. Jensen

```json
{
  "slug": "gitte-jensen",
  "fullName": "Gitte S. Jensen",
  "firstName": "Gitte",
  "lastName": "Jensen",
  "title": "Founder & Research Director, NIS Labs",
  "bio": "PhD, cellular immunologist. Founder of NIS Labs (Natural Immune Systems Labs) in Klamath Falls, OR. 100+ publications. Primary research collaborator of Christian Drapeau on stem cell mobilization studies.",
  "websiteUrl": "https://nislabs.com",
  "expertiseAreas": ["cellular immunology", "stem cell mobilization", "flow cytometry", "natural products research"]
}
```

## Organizations

### STEMREGEN / Kalyagen

```json
{
  "slug": "stemregen-kalyagen",
  "name": "STEMREGEN",
  "legalName": "Biomics, LLC (DBA Kalyagen)",
  "organizationType": "BRAND",
  "description": "Direct-to-consumer supplement brand founded by Christian Drapeau in 2016. Sells plant-based formulations positioned around Endogenous Stem Cell Mobilization (ESCM). Products include Release, Signal, Mobilize, and Release SPORT. Legal entity is Biomics LLC (DBA Kalyagen), a Texas LLC. Inc. 5000 honoree in 2024 (#1,765, 297% 3-year growth) and 2025. SEC Form D filings show $564K raised from 3 accredited investors.",
  "websiteUrl": "https://www.stemregen.co",
  "headquarters": "Austin, TX",
  "foundedYear": 2016,
  "aliases": ["Kalyagen", "Kalyagen Inc", "Biomics LLC"],
  "domains": ["stemregen.co"],
  "tags": ["supplements", "stem-cells", "D2C", "biohacking", "longevity"]
}
```

### STEMTech International

```json
{
  "slug": "stemtech-international",
  "name": "STEMTech International",
  "organizationType": "BRAND",
  "description": "Defunct MLM supplement company co-founded by Christian Drapeau (~2005). Marketed StemEnhance (AFA-based stem cell mobilizer). Filed Chapter 11 bankruptcy in February 2017. Predecessor to STEMREGEN/Kalyagen.",
  "aliases": ["STEMTech HealthSciences", "Stemtech Corporation", "STEK"],
  "tags": ["supplements", "stem-cells", "MLM", "defunct"]
}
```

## Products

### STEMREGEN Release

```json
{
  "slug": "stemregen-release",
  "name": "STEMREGEN Release",
  "organizationId": "stemregen-kalyagen",
  "category": "supplement",
  "description": "Core stem cell mobilizer in the STEMREGEN protocol. 7-ingredient capsule blend containing SeaStem (sea buckthorn), StemAloe (Madagascar aloe), StemAFA (AFA), Fucus vesiculosus, Panax notoginseng, beta-1,3-glucan, and fractionated colostrum. Positioned to release stem cells from bone marrow and support migration into tissues.",
  "price": 189,
  "currency": "USD",
  "productUrl": "https://www.stemregen.co/products/release",
  "tags": ["stem-cells", "mobilization", "capsules"],
  "benefits": ["Stem cell release", "Stem cell migration", "Healthy aging support"]
}
```

### STEMREGEN Release SPORT

```json
{
  "slug": "stemregen-sport",
  "name": "STEMREGEN Release SPORT",
  "organizationId": "stemregen-kalyagen",
  "category": "supplement",
  "description": "Athletic-positioned variant of STEMREGEN Release. NSF Certified for Sport (WADA compliant). Replaces fractionated colostrum with pterostilbene. Same remaining 6 ingredients as Release.",
  "price": 189,
  "currency": "USD",
  "productUrl": "https://www.stemregen.co/products/sport",
  "tags": ["stem-cells", "sport", "recovery", "NSF-certified"],
  "benefits": ["Stem cell release", "Athletic recovery", "NSF Certified for Sport"]
}
```

### STEMREGEN Signal

```json
{
  "slug": "stemregen-signal",
  "name": "STEMREGEN Signal",
  "organizationId": "stemregen-kalyagen",
  "category": "supplement",
  "description": "Anti-inflammatory product in the STEMREGEN protocol. 10-ingredient tablet blend including bromelain, curcumin (98%), phycocyanin (30%), pterostilbene (98%), astaxanthin (4%), and piperine (98%). Positioned to reduce cytokine noise and improve stem cell homing signal clarity.",
  "price": 134,
  "currency": "USD",
  "productUrl": "https://www.stemregen.co/products/signal",
  "tags": ["anti-inflammatory", "signal", "cytokines"],
  "benefits": ["Enhanced signal clarity", "Rapid recovery", "Reduced signaling noise"]
}
```

### STEMREGEN Mobilize

```json
{
  "slug": "stemregen-mobilize",
  "name": "STEMREGEN Mobilize",
  "organizationId": "stemregen-kalyagen",
  "category": "supplement",
  "description": "Vascular support product in the STEMREGEN protocol. 14-ingredient stick pack blend including nattokinase, NAC, hydroxytyrosol, fucoidan, StemAFA, beetroot nitrate, and L-citrulline. Positioned to support microcirculation, capillary integrity, endothelial glycocalyx, and nitric oxide production.",
  "price": 164,
  "currency": "USD",
  "productUrl": "https://www.stemregen.co/products/mobilize",
  "tags": ["microcirculation", "glycocalyx", "nitric-oxide", "vascular"],
  "benefits": ["Enhanced microcirculation", "Capillary support", "Glycocalyx health"]
}
```

## Case Studies

### SBB-PE RCT (PMID 30787601)

```json
{
  "slug": "sbb-pe-rct-2019",
  "title": "Rapid and selective mobilization of specific stem cell types after consumption of a polyphenol-rich extract from sea buckthorn berries (Hippophae) in healthy human subjects",
  "studyType": "Randomized Controlled Trial (crossover)",
  "doi": "10.2147/CIA.S186893",
  "journal": "Clinical Interventions in Aging",
  "publicationDate": "2019-01-28T00:00:00Z",
  "sourceUrl": "https://pubmed.ncbi.nlm.nih.gov/30787601/",
  "outcomeSummary": "n=12 healthy adults; 500mg SBB-PE vs placebo crossover; reported 24-33% increases in circulating stem cell subpopulations at 1-2 hours. Surrogate endpoint only (flow cytometry counts). No clinical outcomes. Commercially-affiliated investigators.",
  "tags": ["RCT", "sea-buckthorn", "SBB-PE", "stem-cell-mobilization", "pilot"],
  "keywords": ["stem cell mobilization", "sea buckthorn", "CD34", "flow cytometry", "polyphenols"]
}
```

### NCT04515537 (AFA + SVF in Heart Failure)

```json
{
  "slug": "nct04515537-afa-svf-hf",
  "title": "Cyanophyta Aphanizomenon flos-aquae, and Adipose Stroma Vascular Fraction, in Heart Failure Patient",
  "studyType": "Interventional (registered as observational)",
  "sourceUrl": "https://clinicaltrials.gov/study/NCT04515537",
  "outcomeSummary": "N=15 ischemic HF patients; 3 arms (AFA, SVF, AFA+SVF); primary completion Dec 2022. Status: UNKNOWN. No results posted. No publications found. Almost certainly uses Kalyagen/STEMREGEN AFA product based on sister trial evidence.",
  "tags": ["clinical-trial", "heart-failure", "AFA", "SVF", "Spain", "abandoned"],
  "keywords": ["heart failure", "AFA", "SVF", "stem cell mobilization", "STEMREGEN"]
}
```

## Compounds (for future ingestion)

Key compounds to create as `Compound` entities:

| Slug | Name | Canonical Name |
|------|------|---------------|
| aphanizomenon-flos-aquae | Aphanizomenon flos-aquae | AFA |
| sea-buckthorn-sbb-pe | Sea Buckthorn Polyphenol Extract | SBB-PE |
| fucoidan | Fucoidan | Fucoidan |
| beta-1-3-glucan | Beta-1,3-Glucan | β-(1→3)-D-Glucan |
| phycocyanin | Phycocyanin | C-Phycocyanin |
| pterostilbene | Pterostilbene | Pterostilbene |
| hydroxytyrosol | Hydroxytyrosol | 3,4-DHPEA |
| nattokinase | Nattokinase | Subtilisin NAT |
| astaxanthin | Astaxanthin | Astaxanthin |
| ginsenoside-rg1 | Ginsenoside Rg1 | Ginsenoside Rg1 |
| curcumin | Curcumin | Diferuloylmethane |

## Related Notes

- [[stemregen-kalyagen-synthesis|STEMREGEN / Kalyagen Synthesis]]
- [[MISSION-001-stemregen-deep-dive|Mission Brief]]
