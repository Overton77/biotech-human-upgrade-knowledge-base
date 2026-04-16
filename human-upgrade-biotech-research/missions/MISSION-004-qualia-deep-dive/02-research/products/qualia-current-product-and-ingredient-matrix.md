---
type: research
title: "Qualia current product and ingredient matrix"
created: 2026-04-15
updated: 2026-04-15
mission: MISSION-004-qualia-deep-dive
episode: "1296"
episode_id: "692b8834004e71ed86aa1e6c"
tags: [research, qualia, products, ingredients, catalog]
confidence: medium
---

# Qualia current product and ingredient matrix

## Bottom line

Qualia's current public catalog is broader than the initial seed implied. The strongest public current-state stack combines brain products (`Mind`, `Mind Caffeine Free`), healthy-aging products (`Mitochondria+`, `NAD+`, `Senolytic`, `Joint Health`, `Stem Cell`, `Creatine+`), sleep products (`Magnesium+`, `Night`), and digestion (`Probiotic+`). Ingredient transparency is strongest on `Joint Health`, `NAD+`, `Mitochondria+`, `Magnesium+`, `Creatine+`, `Mind`, and `Mind Caffeine Free`, while exact one-time pricing remains incomplete for several products because later browser checks started hitting Cloudflare limits.

## High-Signal Matrix

| Product | Current position | Ingredient completeness | Pricing completeness | Notable branded ingredients or compounds | Main caution |
|------|------|------|------|------|------|
| [[qualia-joint-health]] | Healthy-aging / mobility flagship | High | High | [[ovomet]], [[tamaflex]], [[apresflex]], GingerT3, CuberUp, boron, L-carnitine | Strong branded-ingredient transparency, but deeper claim-evidence mapping still needed |
| Qualia Senolytic | Healthy-aging / intermittent senolytic | Medium | Medium | 9-ingredient senolytic blend; exact full table not captured in this pass | Live page validated, but Cloudflare blocked later follow-up |
| Qualia Mitochondria+ | Cellular-energy / longevity flagship | Medium-High | High | 34 ingredients; creatine monohydrate, cocoa extract, rosemary extract, Aquamin magnesium, B-vitamin stack | Large formula needs a dedicated evidence pass to separate whole-product claims from ingredient proxies |
| Qualia NAD+ | NAD / longevity flagship | High | High | NIAGEN, niacinamide, niacin, resveratrol, Coffeeberry and additional support ingredients | Strong company-led claim language; independent validation still needs PubMed pass |
| Qualia Magnesium+ | Sleep / calm / cognition support | Medium-High | High | 10 forms of magnesium, Aquamin, boron, trace mineral complex | Public page is strong, but ingredient-by-ingredient evidence still open |
| Qualia Creatine+ | Strength / brain / healthy-aging support | High | Medium | OptiCreatine, Creatine MagnaPower, sea salt | Exact current one-time price still not captured |
| Qualia Mind | Brain / memory flagship | High | Low-Medium | Nutricog, RealLionsMane, Coffeeberry, Cognizin, Sabroxy, SmartSeed, alpha-GPC, phosphatidylserine | Price not reliably captured in this pass despite strong ingredient table extraction |
| Qualia Mind Caffeine Free | Brain / memory alternative | High | Low | enXtra, RealLionsMane, Cognizin, Sabroxy, SmartSeed, alpha-GPC, phosphatidylserine | Same pricing gap as Mind |
| Qualia Stem Cell | Regenerative-aging lane | Medium | Low | CyanthOx, AFAninPlus, Alomac, Wellmune, Nucleoprime and more | The public page remains active, but this is a claim-sensitive product needing stronger evidence review |
| Qualia Night | Sleep support | Medium | Medium | VINEATROL20, KSM-66, holy basil, reishi and more | Exact serving/count details still partial |
| Qualia Probiotic+ | Gut / gut-brain / digestion | Medium | Low | DigeZyme, Fermeric, baobab and related gut-support ingredients | One-time price missing; probiotic/postbiotic breakdown deserves a follow-up |

## Product-Line Read

### Strongest current commerce signals

- `NAD+`, `Mitochondria+`, `Joint Health`, and `Magnesium+` have the cleanest current live-page validation because rendered browser snapshots captured the purchase options directly.
- `Mind` is still presented as a flagship and is featured on the homepage as `Qualia Mind 2.0`.
- `Senolytic` remains heavily merchandised and positioned as a clinically tested intermittent-use product.

### Strongest current ingredient-transparency signals

- `Joint Health` is the clearest branded-ingredient product in the current catalog.
- `NAD+` is the clearest pathway-based longevity formula in the current catalog, with explicit emphasis on three NAD precursors.
- `Mind` and `Mind Caffeine Free` remain the most ingredient-dense current nootropic products.
- `Creatine+` is unusually simple relative to the rest of the catalog and easier to trace from claims to ingredients.

## Ingredient-Lane Highlights

### Joint Health

- Strongest compound / branded-ingredient lane surfaced in this slice.
- Uses explicit research-anchored dosing logic on official ingredient pages:
  - `Ovomet` `300 mg`
  - `TamaFlex` `250 mg`
  - `ApresFlex` `100 mg`
- This makes `Joint Health` a good anchor product for the ingredient-evidence stage.

### NAD+

- Current page claims `14 ingredients` and `3 NAD+ precursors`.
- Official ingredient page explicitly centers `NIAGEN` and explains why the formula combines niacinamide, niacin, and nicotinamide riboside.
- This is a clean target for later PubMed and sponsorship review.

### Mind / Mind Caffeine Free

- Both retain broad multi-ingredient nootropic architecture.
- `Mind Caffeine Free` replaces stimulant caffeine sources with `enXtra`, giving a useful compare/contrast product pair inside the same product family.

## Contradictions / Gaps To Preserve

- Some product pages expose exact one-time prices cleanly while others did not in this pass because rendered follow-up became rate-limited.
- `Mind` and `Mind Caffeine Free` ingredient capture is strong, but pricing capture is incomplete.
- `Stem Cell` and `Probiotic+` remain active public products, but their exact current pricing and some package details still need a second rendered-page pass.

## Recommended Next Research Steps

- [high] Run a PubMed-backed evidence pass for `Joint Health`, starting with [[ovomet]], [[tamaflex]], and [[apresflex]].
- [high] Run a separate evidence pass for `Qualia NAD+`, especially around `NIAGEN`, claimed `67%` NAD+ increase, and commercial-sponsorship links.
- [medium] Return for a second browser pass on `Mind`, `Mind Caffeine Free`, `Creatine+`, `Stem Cell`, and `Probiotic+` once Cloudflare limits cool down.
- [medium] Build dedicated product notes for `Mitochondria+`, `NAD+`, `Mind`, and `Senolytic` if this mission continues past the current product-lane slice.

## Sources

- [[2026-04-15-qualia-current-product-catalog]]
- [[2026-04-15-qualia-company-and-web-footprint]]
