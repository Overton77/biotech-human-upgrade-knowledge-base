---
name: obsidian-vault-research
description: |
  Manage the `human-upgrade-biotech-research` Obsidian vault as the canonical workspace for research missions. Use when starting a mission, placing notes in the correct folder, defining frontmatter, promoting seed material into durable notes, linking evidence, or maintaining provenance across source captures, research notes, syntheses, and entity notes.
---

# Obsidian Vault: human-upgrade-biotech-research

This skill defines the canonical structure and note contracts for the local biotech research vault.

Use this skill for:

- starting a new research mission
- deciding what kind of note to create
- deciding where a note belongs in the vault
- applying vault-specific frontmatter and naming rules
- promoting seed material and starter sources into durable notes
- preserving provenance and research traceability

Do not duplicate lower-level Obsidian instructions here. Delegate compactly:

- `obsidian-markdown` for Obsidian syntax, wikilinks, callouts, embeds, and frontmatter formatting
- `obsidian-cli` for reading, creating, searching, and editing notes through the CLI
- `obsidian-bases` for `.base` files, filtered views, and dashboards
- `obsidian-automation` for larger automation ideas and recurring workflows

## Related Skill Locations

All related local skills live under:

```text
human_upgrade_research/.agents/skills/
```

For obsidian related skills:

- Obsidian CLI folder: `human_upgrade_research/.agents/skills/obsidian-cli/`
- Obsidian CLI file: `human_upgrade_research/.agents/skills/obsidian-cli/SKILL.md`
- Obsidian Markdown folder: `human_upgrade_research/.agents/skills/obsidian-markdown/`
- Obsidian Markdown file: `human_upgrade_research/.agents/skills/obsidian-markdown/SKILL.md`
- Obsidian Bases folder: `human_upgrade_research/.agents/skills/obsidian-bases/`
- Obsidian Bases file: `human_upgrade_research/.agents/skills/obsidian-bases/SKILL.md`
- Obsidian Automation folder: `human_upgrade_research/.agents/skills/obsidian-automation/`
- Obsidian Automation file: `human_upgrade_research/.agents/skills/obsidian-automation/SKILL.md`

For the broader research workflow that feeds this vault, also see:

- Biotech Deep Research folder: `human_upgrade_research/.agents/skills/biotech-deep-research/`
- Biotech Deep Research file: `human_upgrade_research/.agents/skills/biotech-deep-research/SKILL.md`

## Vault Location

Vault root:

```text
human_upgrade_research/human-upgrade-biotech-research/
```

Absolute path:

```text
C:\Users\Pinda\Proyectos\humanupgradeapp\human_upgrade_research\human-upgrade-biotech-research\
```

## Core Model

This vault is the canonical human-readable workspace for biotech research missions.

Research may begin from any combination of:

- episode files or episode seed folders in `human_upgrade_seeds/`
- instructional content or prior mission notes
- externally captured web sources
- prior entity notes, syntheses, or research notes
- ad hoc user-provided starter documents

Typical mission subjects include:

- biotech entities from research through consumer products
- people, organizations, products, compounds, and studies
- technologies, mechanisms, protocols, and claims
- stories, timelines, controversies, and business context
- case studies, clinical trials, and related evidence

The vault is mission-container-first:

- keep `00-inbox/` at the root for global intake and routing
- keep `05-ontology/` and `06-prompts-rules/` at the root as shared global guidance
- store actual mission work under `missions/MISSION-NNN-slug/`
- inside each mission container, use the lifecycle folders `00-inbox` through `04-entities`
- keep notes mission-scoped by default instead of scattering them into root-level global category folders
- only promote notes into a future cross-mission library when they are genuinely reused across missions

## Canonical Folders

Treat these folders as canonical even if some are empty.

| Folder | Purpose | What belongs here |
|--------|---------|-------------------|
| `00-inbox` | Global intake and routing | Root inbox, mission index notes, vault-level routing notes |
| `missions/` | Mission containers | One folder per mission, e.g. `missions/MISSION-001-stemregen-deep-dive/` |
| `missions/MISSION-NNN-slug/00-inbox` | Mission intake | Mission brief and mission-scoped intake notes |
| `missions/MISSION-NNN-slug/01-sources/raw-json` | Mission raw captures | Tavily, Firecrawl, browser, API, MCP, and export dumps for that mission |
| `missions/MISSION-NNN-slug/01-sources/markdown` | Mission source notes | Human-readable normalized source notes for that mission |
| `missions/MISSION-NNN-slug/01-sources/media` | Mission media assets | Image URLs, PDF URLs, downloadable document references, diagrams, and media indexes |
| `missions/MISSION-NNN-slug/02-research` | Mission analysis | Working analysis, timelines, claim reviews, comparisons, ingestion prep |
| `missions/MISSION-NNN-slug/03-syntheses` | Mission conclusions | Mission syntheses, uncertainty summaries, wrap-ups |
| `missions/MISSION-NNN-slug/04-entities/people` | Mission-scoped people | Person notes created for that mission |
| `missions/MISSION-NNN-slug/04-entities/organizations` | Mission-scoped organizations | Organization notes created for that mission |
| `missions/MISSION-NNN-slug/04-entities/products` | Mission-scoped products | Product notes created for that mission |
| `missions/MISSION-NNN-slug/04-entities/compounds` | Mission-scoped compounds | Compound notes when they deserve dedicated treatment in that mission |
| `missions/MISSION-NNN-slug/04-entities/studies` | Mission-scoped studies | Trial, study, and case-study notes for that mission |
| `05-ontology` | Shared schema and taxonomy | Entity definitions, normalization rules, naming policies, relationship models, Bases views if appropriate |
| `06-prompts-rules` | Reusable vault guidance | Templates, checklists, prompt fragments, provenance rules, mission standards |

## Mission Start Workflow

When starting a new mission:

1. Create a mission container at `missions/MISSION-NNN-slug/`.
2. Create the mission note at `missions/MISSION-NNN-slug/00-inbox/MISSION-NNN-slug.md`.
3. Record the mission objective, scope, exclusions, deliverables, and starter inputs.
4. Organize mission artifacts inside that mission container rather than placing them in root-level category folders.
5. Keep the root `00-inbox/` for global routing and mission discovery, not for storing the full mission body.

Starter inputs can include:

- seed folder paths such as `human_upgrade_seeds/episode-seeds/...`
- episode numbers and episode IDs
- episode markdown stubs
- instructional content and user constraints
- URLs, PDFs, screenshots, exports, or prior notes

Mission notes should explicitly capture:

- the mission objective
- starter material and file paths
- the target entities or technologies
- what is in scope and out of scope
- research lanes such as person, company, product, compound, study, claim, timeline, or controversy
- deliverables and a status log

## Choosing The Right Note Type

Use this decision rule:

- root `00-inbox` when the note is vault-level intake, routing, or meta guidance
- `missions/MISSION-NNN-slug/00-inbox` when the note is mission control for a specific mission
- `missions/MISSION-NNN-slug/01-sources/raw-json` when the artifact is a machine-generated raw capture for that mission
- `missions/MISSION-NNN-slug/01-sources/markdown` when the artifact is a cleaned, human-readable mission source note
- `missions/MISSION-NNN-slug/02-research` when the note is analytical, comparative, provisional, or mission-specific
- `missions/MISSION-NNN-slug/03-syntheses` when the note states conclusions across multiple mission sources or research notes
- `missions/MISSION-NNN-slug/04-entities/*` when the note is a mission-scoped entity page
- `05-ontology` when the note defines taxonomy, schemas, naming, or normalization
- `06-prompts-rules` when the note defines reusable operating rules, templates, or prompt guidance

Do not force every concept into an entity note:

- technologies, mechanisms, and protocols usually begin in `missions/MISSION-NNN-slug/02-research`
- stories and timelines usually belong in `missions/MISSION-NNN-slug/02-research` or `missions/MISSION-NNN-slug/03-syntheses`
- compounds move to `missions/MISSION-NNN-slug/04-entities/compounds` only when they are reusable beyond one note inside that mission

## Frontmatter Standards

Every note must have YAML frontmatter.

### Shared Fields

Use these wherever they make sense:

```yaml
created: YYYY-MM-DD
updated: YYYY-MM-DD
tags: [tag-a, tag-b]
confidence: high | medium | low
mission: MISSION-NNN-slug
episode: "1374"
episode_id: "mongo-or-source-id"
seed_folder: "human_upgrade_seeds/episode-seeds/..."
timeframe: "current" | "YYYY-YYYY" | "YYYY-MM-DD to YYYY-MM-DD"
```

Not every field is required on every note, but mission linkage should be preserved whenever the note was created as part of a mission.

### Mission Note (`missions/MISSION-NNN-slug/00-inbox`)

```yaml
---
type: mission
status: active | complete | paused
created: YYYY-MM-DD
updated: YYYY-MM-DD
episode: "1374"
episode_id: "source-id"
seed_folder: "human_upgrade_seeds/episode-seeds/..."
timeframe: "current"
tags: [mission, topic-tags]
---
```

### Source Note (`missions/MISSION-NNN-slug/01-sources/markdown`)

```yaml
---
type: source
title: "Source Title"
sourceUrl: "https://..."
accessDate: YYYY-MM-DD
sourceType: website | paper | registry | filing | interview | export
mission: MISSION-NNN-slug
episode: "1374"
episode_id: "source-id"
timeframe: "current"
assetUrls:
  - "https://example.com/file.pdf"
  - "https://example.com/image.png"
tags: [source, topic-tags]
confidence: high | medium | low
---
```

Use `assetUrls` when the source yields important media or documents such as:

- product images
- diagrams or charts
- downloadable PDFs
- investor decks, labels, filings, or brochures

### Research Note (`missions/MISSION-NNN-slug/02-research`)

```yaml
---
type: research
title: "Descriptive Title"
created: YYYY-MM-DD
updated: YYYY-MM-DD
mission: MISSION-NNN-slug
episode: "1374"
episode_id: "source-id"
tags: [research, topic-tags]
confidence: high | medium | low
---
```

### Synthesis Note (`missions/MISSION-NNN-slug/03-syntheses`)

```yaml
---
type: synthesis
title: "Descriptive Title"
created: YYYY-MM-DD
updated: YYYY-MM-DD
mission: MISSION-NNN-slug
episode: "1374"
episode_id: "source-id"
tags: [synthesis, topic-tags]
confidence: high | medium | low
---
```

Mission wrap-ups and synthesis notes should usually end with:

- `## Unresolved Questions`
- `## Next Steps / Recommendations`

### Entity Notes (`missions/MISSION-NNN-slug/04-entities/*`)

Entity notes share a common core and then add type-specific fields.

Common entity fields:

```yaml
---
type: person | organization | product | compound | study
slug: kebab-case-identifier
created: YYYY-MM-DD
updated: YYYY-MM-DD
tags: [type, domain-tags]
confidence: high | medium | low
mission: MISSION-NNN-slug
episode: "1374"
episode_id: "source-id"
---
```

Person note example:

```yaml
---
type: person
slug: christian-drapeau
fullName: Christian Drapeau
firstName: Christian
lastName: Drapeau
title: "Founder & Chief Science Officer, STEMREGEN"
tags: [person, founder, scientist]
created: 2026-04-07
updated: 2026-04-07
confidence: high
---
```

Organization note example:

```yaml
---
type: organization
slug: stemregen-kalyagen
name: "STEMREGEN / Kalyagen"
legalName: "Biomics, LLC (DBA Kalyagen)"
organizationType: BRAND
tags: [organization, brand]
created: 2026-04-07
updated: 2026-04-07
confidence: high
---
```

Product note example:

```yaml
---
type: product
slug: stemregen-release
name: "STEMREGEN Release"
category: supplement
organizationId: stemregen-kalyagen
price: 189
currency: USD
tags: [product, supplement]
created: 2026-04-07
updated: 2026-04-07
confidence: high
---
```

Study note example:

```yaml
---
type: study
slug: sbb-pe-rct-pmid-30787601
title: "SBB-PE Stem Cell Mobilization RCT"
studyType: "Randomized Controlled Trial (crossover)"
pmid: "30787601"
doi: "10.2147/CIA.S186893"
nctId: "NCT03388073"
journal: "Clinical Interventions in Aging"
year: 2019
tags: [study, rct]
created: 2026-04-07
updated: 2026-04-07
confidence: high
---
```

Use the field that matches the note type:

- people usually use `fullName`
- organizations and products usually use `name`
- research, synthesis, and source notes usually use `title`
- studies often use `title` plus structured identifiers like `pmid`, `pmcid`, `nctId`, `doi`

## Naming And Placement Rules

Use kebab-case filenames unless the folder convention explicitly uses a mission prefix.

Canonical patterns:

- mission notes: `MISSION-NNN-slug.md`
- mission containers: `missions/MISSION-NNN-slug/`
- people: `firstname-lastname.md`
- organizations: `brand-name.md` or `brand-parent.md`
- products: `brand-product.md`
- compounds: `compound-name.md`
- studies: `nct-id-or-pmid-based-slug.md`
- research notes: descriptive analysis slugs inside mission lane folders, such as `02-research/compounds/compound-analysis.md` or `02-research/science/escm-science-review.md`
- synthesis notes: descriptive synthesis slugs inside the mission synthesis folder, such as `03-syntheses/stemregen-kalyagen-synthesis.md`

## Linking Rules

Use Obsidian wikilinks for internal vault references.

```markdown
[[christian-drapeau]]
[[christian-drapeau|Christian Drapeau]]
[[stemregen-kalyagen|STEMREGEN / Kalyagen]]
```

Linking expectations:

- mission notes link to starter material, key research notes, and target entities
- source notes link to the mission and the entities they inform
- research notes link to all entities, studies, and source notes they discuss
- synthesis notes link to the major supporting research and entity notes
- entity notes include a `## Related Notes` section

Use standard Markdown links only for external URLs.

## Provenance Rules

Every substantive claim must be traceable.

Always include:

- URLs, PMIDs, DOIs, NCT IDs, or filing references
- access dates for web sources
- explicit `[UNVERIFIED]` markers when a claim is not yet confirmed
- confidence and evidence language that matches the underlying source quality

Preferred evidence labels:

- `Company-asserted`
- `Peer-reviewed`
- `Registry`
- `Independent`
- `Regulatory`
- `Financial filing`

If evidence conflicts:

- preserve both sides
- state the conflict explicitly
- do not flatten disagreement into a single confident claim

## Raw Capture Rules

Preferred location for durable raw artifacts:

- `missions/MISSION-NNN-slug/01-sources/raw-json/` for JSON or structured machine outputs
- `missions/MISSION-NNN-slug/01-sources/markdown/` for readable source notes derived from those artifacts
- `missions/MISSION-NNN-slug/01-sources/media/` for media/document URL indexes or mission-specific asset notes

If a tool writes outside the vault, such as repo-level capture folders, do not lose the chain of custody:

- either copy the durable artifact into `01-sources/raw-json/`
- or create a source note that records the external path and links the artifact to the mission

Important captures should have both:

- a raw artifact
- a readable source note summarizing what the artifact contains
- any important media/document URLs preserved in the readable note when they materially support the mission

## Promotion Rules

Promote notes forward only when they become more stable.

Use these rules:

- mission work is mission-scoped by default and belongs under `missions/MISSION-NNN-slug/`
- starter materials and mission instructions begin in `missions/MISSION-NNN-slug/00-inbox`
- raw captures become `missions/MISSION-NNN-slug/01-sources/*`
- provisional analysis becomes `missions/MISSION-NNN-slug/02-research`
- mission-scoped entities become `missions/MISSION-NNN-slug/04-entities/*`
- cross-source mission conclusions become `missions/MISSION-NNN-slug/03-syntheses`
- keep the root `00-inbox`, `05-ontology`, and `06-prompts-rules` for global use
- do not scatter mission-only notes into root-level `01`-`04` folders

Compound promotion rule:

- keep compounds inside mission research notes when they are only supporting one mission-specific analysis
- create `missions/MISSION-NNN-slug/04-entities/compounds/<slug>.md` when the compound is reused across products, studies, or analyses within that mission
- only promote beyond the mission container when the compound becomes genuinely cross-mission

## Note Quality Bar

Default standards:

- prefer structured tables over long prose when comparing evidence
- include `## Sources` on entity, research, and synthesis notes when relevant
- include `## Related Notes` on entity notes
- include `## Unresolved Questions` when important gaps remain
- include `## Next Steps / Recommendations` on synthesis notes and mission wrap-ups when follow-up work is logically warranted
- update existing durable notes instead of creating near-duplicates
- keep mission-specific speculation in research notes, not entity notes

## What Belongs In `05-ontology` And `06-prompts-rules`

Use `05-ontology` for:

- entity taxonomy
- relationship definitions
- normalization rules
- naming and slug policy
- shared dashboards or Bases views when they are part of the vault schema layer

Use `06-prompts-rules` for:

- mission templates
- source note templates
- entity note checklists
- provenance checklists
- reusable agent prompt fragments and operating rules

## Practical Rule Of Thumb

This skill answers:

- what note should exist
- where it should live
- what metadata it should carry
- how it should link to the rest of the vault

For syntax, CLI mechanics, Bases definitions, and automation details, defer to the dedicated Obsidian skills instead of repeating them here.
