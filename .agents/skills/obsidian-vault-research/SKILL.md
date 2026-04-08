---
name: obsidian-vault-research
description: |
  Manage the human-upgrade-biotech-research Obsidian vault — create notes, maintain folder structure, use proper frontmatter, apply Obsidian-style wikilinks, and follow provenance standards. Use when creating research notes, entity notes, source captures, synthesis documents, mission briefs, or any note that belongs in the vault. Triggers on "vault", "obsidian", "note", "entity", "research note", "source note", "synthesis", "mission brief", or when writing structured research output.
---

# Obsidian Vault: human-upgrade-biotech-research

## Vault Location

```
human_upgrade_research/human-upgrade-biotech-research/
```

Relative to workspace root: `C:\Users\Pinda\Proyectos\humanupgradeapp\human_upgrade_research\human-upgrade-biotech-research\`

## Folder Structure

| Folder | Purpose | What goes here |
|--------|---------|----------------|
| `00-inbox` | Mission briefs, intake | Mission notes (MISSION-NNN-slug.md), research tasks, starting questions |
| `01-sources/raw-json` | Machine-generated captures | Raw Tavily, Firecrawl, browser extraction JSON outputs |
| `01-sources/markdown` | Normalized source notes | Cleaned readable source documents with provenance metadata |
| `02-research` | Working research | Comparisons, timelines, evidence gathering, open questions, compound analyses |
| `03-syntheses` | Polished conclusions | Synthesis documents, uncertainty summaries, knowledge gap reports |
| `04-entities/people` | Person entities | One note per person (slug as filename) |
| `04-entities/organizations` | Organization entities | One note per org |
| `04-entities/products` | Product entities | One note per product |
| `04-entities/compounds` | Compound entities | One note per compound |
| `04-entities/studies` | Study/trial entities | One note per study (RCT, clinical trial, case study) |
| `05-ontology` | Schema definitions | Entity types, taxonomy, relationship definitions, normalization rules |
| `06-prompts-rules` | Vault rules | Templates, naming conventions, provenance standards |

## Frontmatter Standards

Every note MUST have YAML frontmatter. Required fields vary by type:

### Mission Note (`00-inbox`)
```yaml
---
type: mission
status: active | complete | paused
created: YYYY-MM-DD
tags: [mission, topic-tags]
---
```

### Entity Note (`04-entities/*`)
```yaml
---
type: person | organization | product | compound | study
slug: kebab-case-identifier
name: "Display Name"
tags: [type, domain-tags]
created: YYYY-MM-DD
updated: YYYY-MM-DD
confidence: high | medium | low
---
```

### Research Note (`02-research`)
```yaml
---
type: research
title: "Descriptive Title"
tags: [research, topic-tags]
created: YYYY-MM-DD
updated: YYYY-MM-DD
confidence: high | medium | low
---
```

### Synthesis Note (`03-syntheses`)
```yaml
---
type: synthesis
title: "Descriptive Title"
tags: [synthesis, topic-tags]
created: YYYY-MM-DD
updated: YYYY-MM-DD
confidence: high | medium | low
---
```

### Source Note (`01-sources/markdown`)
```yaml
---
type: source
title: "Source Title"
sourceUrl: "https://..."
accessDate: YYYY-MM-DD
tags: [source, topic-tags]
---
```

## Linking Rules

Use **Obsidian wikilinks** extensively to connect notes:

```markdown
[[slug-name|Display Name]]       # Link with alias
[[slug-name]]                     # Link using filename
```

**Linking patterns:**
- Entity notes link to related entities: `[[christian-drapeau|Christian Drapeau]]`
- Research notes link to entities they discuss
- Synthesis notes link to all supporting research and entity notes
- Every entity note has a `## Related Notes` section at the bottom

**Slug conventions:**
- People: `firstname-lastname` (e.g., `christian-drapeau`)
- Organizations: `brand-name` or `brand-parent` (e.g., `stemregen-kalyagen`)
- Products: `brand-product` (e.g., `stemregen-release`)
- Compounds: `compound-name` (e.g., `beta-1-3-glucan`)
- Studies: `identifier-or-slug` (e.g., `sbb-pe-rct-pmid-30787601`)

## Provenance Standards

1. **Every claim needs a source.** Use PMIDs, DOIs, URLs, or explicit `[UNVERIFIED]` markers.
2. **Distinguish evidence tiers:**
   - `Company-asserted` — from marketing or company materials
   - `Peer-reviewed` — PubMed-indexed with PMID
   - `Registry` — ClinicalTrials.gov with NCT ID
   - `Independent` — not affiliated with the product company
3. **Track confidence** in frontmatter: `high`, `medium`, `low`
4. **Preserve timestamps:** access dates on sources, publication dates on studies
5. **Record conflicts explicitly.** If evidence disagrees, note both sides.

## Mission Workflow

When starting a new research mission:

1. Create `00-inbox/MISSION-NNN-slug.md` with objectives, stages, entity targets
2. Include a status log table at the bottom
3. Update status as work progresses: `active` → `complete`
4. Track deliverables with checkboxes

## Note Quality Bar

- Structured tables over prose walls
- Evidence assessment tables for products/claims
- `## Related Notes` section on every entity note
- `## Sources` section with URLs on every entity note
- `## Unresolved Questions` when gaps exist
- No duplicative note sprawl — update existing notes rather than creating new ones

## Raw Source Dumps

When capturing raw data (Tavily, Firecrawl, API responses):
- Save JSON to `01-sources/raw-json/` with descriptive filenames
- Create a companion readable note in `01-sources/markdown/` if the data is important
- Reference the raw file from the markdown note
