---
name: biotech-deep-research
description: |
  Conduct mission-driven biotech and human performance research for the Human Upgrade ecosystem. Use when launching or advancing a research mission about people, organizations, products, compounds, technologies, claims, studies, stories, case studies, or business context. This skill acts as the mission conductor: bootstrap the mission, prioritize Tavily for web discovery, use MCP servers for evidence and enrichment, escalate to Firecrawl or browser automation only when needed, produce vault outputs, and finish with unresolved questions plus official next steps and recommendations.
---

# Biotech Deep Research

This skill is the mission conductor for research work in `human_upgrade_research`.

It should not try to replace the specialized skills. Instead, it decides:
- what kind of mission is being run
- which research lanes are needed
- which tool stack to use first
- what artifacts must be written into the vault
- when the mission is mature enough for ingestion handoff

Delegate rather than duplicate:
- `obsidian-vault-research` for vault placement, note contracts, frontmatter, and promotion rules
- `graphql-ingestion` for GraphQL ingestion strategy and MCP usage
- `tavily-search`, `tavily-extract`, `tavily-map`, `tavily-crawl`, `tavily-research` for Tavily workflows
- `firecrawl` for supplementary scrape/download workflows
- `agent-browser` for browser automation when interaction is necessary
- built-in Cursor `WebSearch`, `WebFetch`, and browser tools as supplementary fallbacks or quick checks

## Skill Locations

All local research skills referenced by this skill live under:

```text
human_upgrade_research/.agents/skills/
```

Use these exact folder and file paths:

### Tavily skills

- Folder: `human_upgrade_research/.agents/skills/tavily-cli/`
  File: `human_upgrade_research/.agents/skills/tavily-cli/SKILL.md`
- Folder: `human_upgrade_research/.agents/skills/tavily-best-practices/`
  File: `human_upgrade_research/.agents/skills/tavily-best-practices/SKILL.md`
- Folder: `human_upgrade_research/.agents/skills/tavily-search/`
  File: `human_upgrade_research/.agents/skills/tavily-search/SKILL.md`
- Folder: `human_upgrade_research/.agents/skills/tavily-extract/`
  File: `human_upgrade_research/.agents/skills/tavily-extract/SKILL.md`
- Folder: `human_upgrade_research/.agents/skills/tavily-map/`
  File: `human_upgrade_research/.agents/skills/tavily-map/SKILL.md`
- Folder: `human_upgrade_research/.agents/skills/tavily-crawl/`
  File: `human_upgrade_research/.agents/skills/tavily-crawl/SKILL.md`
- Folder: `human_upgrade_research/.agents/skills/tavily-research/`
  File: `human_upgrade_research/.agents/skills/tavily-research/SKILL.md`

### Browser and scrape skills

- Folder: `human_upgrade_research/.agents/skills/agent-browser/`
  File: `human_upgrade_research/.agents/skills/agent-browser/SKILL.md`
- Folder: `human_upgrade_research/.agents/skills/firecrawl/`
  File: `human_upgrade_research/.agents/skills/firecrawl/SKILL.md`

### Obsidian-related skills

- Folder: `human_upgrade_research/.agents/skills/obsidian-vault-research/`
  File: `human_upgrade_research/.agents/skills/obsidian-vault-research/SKILL.md`
- Folder: `human_upgrade_research/.agents/skills/obsidian-cli/`
  File: `human_upgrade_research/.agents/skills/obsidian-cli/SKILL.md`
- Folder: `human_upgrade_research/.agents/skills/obsidian-markdown/`
  File: `human_upgrade_research/.agents/skills/obsidian-markdown/SKILL.md`
- Folder: `human_upgrade_research/.agents/skills/obsidian-bases/`
  File: `human_upgrade_research/.agents/skills/obsidian-bases/SKILL.md`
- Folder: `human_upgrade_research/.agents/skills/obsidian-automation/`
  File: `human_upgrade_research/.agents/skills/obsidian-automation/SKILL.md`

### Ingestion skill

- Folder: `human_upgrade_research/.agents/skills/graphql-ingestion/`
  File: `human_upgrade_research/.agents/skills/graphql-ingestion/SKILL.md`

## Mission Inputs

Accept these inputs explicitly or infer them from the user request:

- `mission_slug` such as `MISSION-002-something`
- `seed_folder` or starter episode path when available
- starter inputs such as episode files, instructional content, URLs, prior notes, or exported files
- topic scope
- target entity types
- exclusions or out-of-scope areas
- timeframe or recency requirement such as `current`, `last 12 months`, or `2019-2024`
- desired depth: `light`, `standard`, or `deep`

Common target entity types:
- person
- organization
- product
- compound
- study
- technology
- protocol
- claim
- story or timeline

## Primary Research Priority Order

Use the tools in this order unless there is a clear reason not to.

### 1. Tavily is the default web research stack

Tavily is the primary search and discovery system for this workflow.

Use this escalation path:
1. `tavily-search` for discovery when no URL is known
2. `tavily-extract` for extracting specific URLs
3. `tavily-map` to find relevant pages on a known domain
4. `tavily-crawl` for bulk site extraction
5. `tavily-research` for multi-source synthesis with citations

Default rule:
- start with Tavily for web discovery and source gathering
- do not start with Firecrawl unless you specifically need Firecrawl behavior

Temporal rule:
- when the mission has a timeframe, encode it into the Tavily request rather than leaving it implicit
- use `--time-range`, `--start-date`, `--end-date`, and finance/news modes when they improve precision
- if the request says `current`, bias queries toward recent coverage, current company state, current product pages, and current trial status
- if the request spans historical and current states, run separate searches for each rather than blending them into one vague query

Media rule:
- Tavily results should be mined not only for text sources but also for media-bearing assets
- prefer searches and extracts that preserve image URLs, PDF URLs, diagrams, downloadable documents, and other high-value media locations
- when a page is important, capture both the content and the media/document URLs associated with it

### 2. Built-in Cursor web tools are secondary helpers

Use built-in Cursor tools for:
- quick fact checks
- lightweight supplemental search
- quick fetches of known URLs
- situations where you want fast in-editor confirmation without spinning up CLI workflows

These are supplementary, not the primary research system.

### 3. Firecrawl is supplementary

Use `firecrawl` when Tavily is not the best fit, especially for:
- downloading a site or section as local files
- scrape-heavy workflows with durable local artifacts
- cases where Firecrawl’s crawl/download model is better than Tavily’s focused extraction
- specialized scrape or interact flows
- extracting or downloading media-rich pages, PDFs, diagrams, and asset-heavy site sections

Do not use Firecrawl as the default first step for general discovery.

### 4. Browser automation is for interaction, not default search

Use `agent-browser` or built-in Cursor browser control when:
- a site requires clicking, filling, pagination, scrolling, or login
- a page is highly dynamic and extraction is incomplete
- you need screenshots, downloads, or interaction traces
- you need to surface image locations, downloadable PDFs, or media that only appears after interaction
- a web workflow requires agentic browser navigation rather than normal search/extract

## MCP Priority

The domain MCP servers are core to the mission, especially for evidence linked to products, compounds, trials, sponsors, and referenced studies.

### PubMed

Use for:
- literature search
- fetching abstracts and full text when available
- related-paper expansion
- publication verification

Default use cases:
- person publication history
- compound mechanism evidence
- product-claim evidence
- follow-up searches from an NCT ID or DOI

### ClinicalTrials.gov

Use for:
- case study and trial discovery
- checking registration details, status, design, sponsors, and results
- tracing whether organizations, products, or compounds are linked to a registry record

Always check this when:
- a company or product references a trial
- a compound is claimed to be clinically studied
- sponsorship or co-sponsorship matters to the claim

### PubChem

Use for:
- compound identity
- synonyms and canonical naming
- CID, structure, bioactivity, safety, and chemistry context

Always use this when compounds are central to the mission.

### Edgar tools

Use for:
- organization background
- filings, fundraising, ownership, and business context
- validating financial or legal claims

Use especially when:
- an organization may be public, fundraising, or filing Form D/SEC materials
- business claims matter to the mission

## Mission Workflow

### Step 1: Bootstrap the mission

Start by applying `obsidian-vault-research`.

Create or update the mission container at `missions/MISSION-NNN-slug/` and the mission note at `missions/MISSION-NNN-slug/00-inbox/MISSION-NNN-slug.md`, then capture:
- objective
- starter inputs
- seed folder or episode linkage
- scope and exclusions
- timeframe or whether the mission is explicitly about the current state
- likely research lanes
- expected outputs

If starter inputs include an episode seed or instructional content, treat those as mission inputs, not as finished research.

### Step 2: Choose research lanes

Do not research everything at once. Select lanes based on the mission.

Common lanes:
- person lane
- organization lane
- product lane
- compound lane
- study or case-study lane
- claim lane
- technology or protocol lane
- story, timeline, or controversy lane
- business and filings lane

Each lane should have:
- a target object
- a source strategy
- temporal assumptions
- a likely output note type
- a stopping condition

### Step 3: Run lane research with the right tools

Use this default pattern:

- web discovery: Tavily first
- literature and registry evidence: PubMed and ClinicalTrials.gov
- compound identity and safety: PubChem
- business validation: Edgar tools
- browser automation only if extraction or interaction requires it
- Firecrawl only when a supplementary scrape/download workflow is better

When time matters:
- convert vague recency language into explicit query constraints
- check current company/product pages separately from historical evidence
- distinguish publication year, trial status date, filing date, and current website state

When media matters:
- intentionally gather URLs for images, diagrams, PDFs, slide decks, labels, filings, and downloadable assets
- preserve those URLs as part of the mission outputs, not just the surrounding text

### Step 4: Parallelize where safe

Parallelize independent lanes, not note editing.

Good parallel splits:

```text
Agent 1: organization and filings
Agent 2: people and publication history
Agent 3: product pages and claims
Agent 4: compounds and chemistry
Agent 5: studies, trials, and sponsorship links
```

Collect findings, then consolidate sequentially into the vault to avoid file conflicts.

### Step 5: Consolidate into vault artifacts

All mission output must land in the vault according to `obsidian-vault-research`.

Required output classes:
- raw captures in `missions/MISSION-NNN-slug/01-sources/raw-json/` when durable artifacts are valuable
- readable source notes in `missions/MISSION-NNN-slug/01-sources/markdown/`
- media/document URLs or asset notes in `missions/MISSION-NNN-slug/01-sources/media/` when relevant
- working analysis in `missions/MISSION-NNN-slug/02-research/`
- durable mission-scoped entity notes in `missions/MISSION-NNN-slug/04-entities/`
- final synthesis in `missions/MISSION-NNN-slug/03-syntheses/`
- ingestion handoff when the mission surfaces GraphQL-ready entities and relationships
- media asset locations such as image URLs, diagram URLs, PDF URLs, and document downloads when they materially support the mission

### Step 6: Finish with unresolved questions and official next steps

Every meaningful mission should end with:
- explicit unresolved questions
- official next steps and recommendations

Do not stop at “research complete” if the natural follow-up is obvious.

## Lane-Specific Guidance

### Person lane

Focus on:
- identity and role
- publication history
- patents, prior ventures, affiliations
- controversies, conflicts, regulatory issues

Suggested sources:
- Tavily for bios, interviews, press, controversies
- PubMed for publications
- browser or web search for patents, public profiles, and media assets such as profile images or downloadable bios

### Organization lane

Focus on:
- legal identity, brand structure, history, team, products
- public claims and supporting evidence
- SEC or fundraising context when relevant
- lawsuits, warnings, settlements, or enforcement actions

Suggested sources:
- Tavily for company discovery and news
- Edgar tools for filings and financial context
- Firecrawl or Tavily extract for website pages, media kits, investor PDFs, and diagram/image assets

### Product lane

Focus on:
- ingredients, formulation, claims, pricing, positioning
- linked studies or company-cited evidence
- whether the company references trials, compounds, or mechanisms

Suggested sources:
- Tavily for discovery and extraction
- Firecrawl when bulk product-page scraping, labels, downloadable PDFs, or image-heavy pages help
- ClinicalTrials.gov and PubMed for linked evidence

### Compound lane

Focus on:
- identity and canonical naming
- safety, bioactivity, mechanism, dose context
- human versus animal evidence
- relationship to product claims

Suggested sources:
- PubChem first for identity and chemistry
- PubMed for mechanism and efficacy evidence
- ClinicalTrials.gov if clinical use is claimed

### Study or case-study lane

Focus on:
- whether the study or trial actually exists
- design, status, endpoints, results, sponsors, and publications
- whether a company, product, or compound is linked directly or only rhetorically

Suggested sources:
- ClinicalTrials.gov first for registry
- PubMed for publication follow-up
- Tavily for press releases, company pages, secondary references, and linked PDFs or media assets

## Evidence Rules

Always preserve the difference between:
- company-asserted claims
- peer-reviewed evidence
- registry evidence
- independent evidence
- regulatory or filing evidence

Every substantive claim should include at least one traceable reference:
- URL
- PMID
- DOI
- NCT ID
- SEC or filing reference

When useful, also preserve:
- image URLs
- PDF URLs
- diagram or chart URLs
- downloadable media/document locations

Mark unverified material explicitly with `[UNVERIFIED]`.

## Evidence Assessment Framework

| Level | Criteria | Example |
|-------|----------|---------|
| **Established** | Multiple strong human studies, meta-analyses, or accepted clinical use | G-CSF for stem cell mobilization |
| **Supported** | Credible human evidence with partial replication or strong registry/literature support | Exercise increases circulating progenitors |
| **Preliminary** | Small, early, commercially linked, or weakly replicated evidence | Small company-linked mobilization trials |
| **Speculative** | Mechanistically plausible but weak or indirect human support | Oral translation from non-oral or preclinical evidence |
| **Unsubstantiated** | No meaningful supporting evidence or major logical leap | Product claim with no supporting literature |

## Conflict And Sponsorship Checks

For any study, trial, or case-study-like object, check:
- is the sponsor or co-sponsor linked to the organization being researched?
- is the compound or product directly involved, or only mentioned rhetorically?
- do authors, labs, or investigators have commercial ties?
- is the finding independently replicated?
- are there missing results, status inconsistencies, or absent publications?

This is especially important when organizations link products or compounds to case studies and trials.

## Official Next Steps / Recommendations

This is a required end-state artifact for substantial missions.

Keep `Unresolved Questions` and `Next Steps / Recommendations` separate:
- unresolved questions describe what is not yet known
- next steps describe what should be done next

The final synthesis or mission wrap-up should include:

```markdown
## Unresolved Questions

- What remains unknown

## Next Steps / Recommendations

- [high] Verify X by doing Y because Z
- [medium] Research A because it is adjacent to B
- [medium] Ingest entity group C once relationship D is confirmed
```

Recommended categories for next steps:
- knowledge gap follow-up
- evidence verification
- adjacent entity expansion
- monitoring or future watchlist
- ingestion readiness
- contradiction resolution

A strong next-step item includes:
- priority
- action
- rationale
- dependency or trigger
- expected output

## Outputs

A completed mission should usually produce:
- mission note update
- source captures
- research notes
- entity notes where warranted
- synthesis note
- explicit unresolved questions
- explicit next steps and recommendations
- ingestion handoff if the mission is mature enough
- a usable set of media/document URLs for important images, diagrams, PDFs, or other supporting assets

## Stop Conditions

Stop and summarize when:
- the requested mission scope is satisfied
- the remaining work is mostly low-value tail chasing
- the evidence ceiling has been reached for now
- the mission has produced useful next steps for future work

Do not keep searching indefinitely once the mission can clearly hand off to synthesis, follow-up research, or ingestion.
