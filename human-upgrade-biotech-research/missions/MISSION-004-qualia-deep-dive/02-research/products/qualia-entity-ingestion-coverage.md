---
type: research
title: "Qualia entity ingestion coverage"
created: 2026-04-15
updated: 2026-04-15
mission: MISSION-004-qualia-deep-dive
episode: "1296"
episode_id: "692b8834004e71ed86aa1e6c"
tags: [research, qualia, entities, ingestion]
confidence: medium
---

# Qualia entity ingestion coverage

## Coverage Summary

- Product entity notes currently present after this round: `11`
- Compound entity notes currently present after this round: `150`
- People entity notes currently present after this round: `9`
- Study entity notes currently present after this round: `19`

## What This Round Added

- Product notes were expanded beyond the initial Joint Health-only state to cover the active current catalog.
- Compound notes were generated from current label-level ingredient rows across the active catalog.
- Additional science-team and leadership people notes were added.
- Official study and case-study pages from the current studies hub were promoted into mission-scoped study notes.

## Remaining Caveats

- Some product pricing remains `[UNVERIFIED in this pass]` where the live page did not yield a clean current one-time price.
- One current `Mitochondria+` ingredient row had a partially corrupted rendered name around `ProcynCi`; the amount and base identity were preserved but should be rechecked if exact label text is required.
- Study notes generated from the studies hub should still be followed by PubMed / sponsor / replication review before any evidence-grade ingestion.

## Sources

- [[2026-04-15-qualia-current-product-catalog]]
- [[2026-04-15-qualia-company-and-web-footprint]]
