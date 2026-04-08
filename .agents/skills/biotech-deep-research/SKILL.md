---
name: biotech-deep-research
description: |
  Conduct professional biotech and human performance research using all available tools — Firecrawl (web scraping/search), PubMed MCP, PubChem MCP, ClinicalTrials.gov MCP, Edgar tools MCP, and built-in browser. Use when researching companies, people, products, compounds, clinical trials, mechanisms of action, efficacy evidence, safety profiles, or business/financial context. Triggers on "research", "investigate", "deep dive", "find studies", "look up compound", "check clinical trials", "company background", "evidence review", or any biotech/health research task.
---

# Biotech Deep Research

## Research Domain

The Human Upgrade biotech and human performance ecosystem: people, companies, products, compounds, devices, protocols, technologies, studies, claims, mechanisms, efficacy, safety, sponsorship, and business context.

## Available Tools

### Primary Web Research

| Tool | When to Use | How |
|------|------------|-----|
| **Firecrawl search** | Find pages, articles, news | `firecrawl search "query" --scrape --limit 5 -o .firecrawl/result.json --json` |
| **Firecrawl scrape** | Extract content from a known URL | `firecrawl scrape "url" --only-main-content -o .firecrawl/page.md` |
| **Firecrawl map** | Discover URLs on a site | `firecrawl map "domain.com" --search "keyword"` |
| **WebSearch** | Quick fact lookup | Built-in Cursor tool |
| **WebFetch** | Fetch a URL as markdown | Built-in Cursor tool |
| **Browser tools** | Interactive pages, JS-heavy sites | `cursor-ide-browser-*` tools |

### Scientific Literature (MCP Servers)

| Server | Key Tools | When to Use |
|--------|-----------|-------------|
| **PubMed** | `pubmed_search_articles`, `pubmed_fetch_articles`, `pubmed_fetch_fulltext`, `pubmed_find_related` | Search/fetch journal articles, get abstracts, full text, citations |
| **PubChem** | `pubchem_search_compounds`, `pubchem_get_compound_details`, `pubchem_get_bioactivity`, `pubchem_get_compound_safety` | Compound identity (CID, SMILES, MW), bioactivity, safety, drug-likeness |
| **ClinicalTrials.gov** | `clinicaltrials_search_studies`, `clinicaltrials_get_study_record`, `clinicaltrials_get_study_results`, `clinicaltrials_find_eligible` | Find trials, get protocols, check status, get results |
| **Edgar tools** | `edgar_company`, `edgar_filing`, `edgar_search`, `edgar_ownership`, `edgar_text_search` | SEC filings, company financials, insider trades, corporate data |

### Subagents

Use `Task` tool with `subagent_type` to parallelize research:
- `generalPurpose` — broad research tasks with web search + MCP access
- `explore` — fast codebase/file exploration
- Launch **multiple agents in parallel** for independent research tracks

## Research Protocol

### For a Person
1. **PubMed**: `pubmed_search_articles` with author name → get PMIDs → `pubmed_fetch_articles`
2. **Web**: Firecrawl search for LinkedIn, bios, interviews, controversies
3. **Patents**: Search Justia patents or Google Patents
4. **Conflicts**: Search for FDA warnings, lawsuits, regulatory actions

### For a Company/Organization
1. **Edgar**: `edgar_company` with ticker or name → financials, filings
2. **Edgar**: `edgar_search` for SEC filings (Form D, 10-K, etc.)
3. **Web**: Firecrawl scrape company website (about, team, products)
4. **Web**: Search for Inc. 5000, Crunchbase, press releases, news
5. **Legal**: Search for lawsuits, Prop 65 settlements, FDA actions

### For a Product/Supplement
1. **Web**: Firecrawl scrape product page → extract ingredients, pricing, claims
2. **PubChem**: Look up each active compound → CID, properties, safety
3. **PubMed**: Search for each ingredient + claimed mechanism
4. **ClinicalTrials.gov**: Search for trials involving the product or ingredients

### For a Compound
1. **PubChem**: `pubchem_search_compounds` by name → `pubchem_get_compound_details` with CID
2. **PubChem**: `pubchem_get_bioactivity` for biological activity profile
3. **PubChem**: `pubchem_get_compound_safety` for GHS hazard data
4. **PubMed**: Search for "[compound] mechanism of action", "[compound] clinical trial"
5. Assess: oral bioavailability, dose-response, human vs animal evidence

### For a Clinical Trial
1. **ClinicalTrials.gov**: `clinicaltrials_get_study_record` with NCT ID
2. **PubMed**: Search for published results by NCT ID or title
3. **PubMed**: `pubmed_find_related` for citing articles
4. Assess: design quality, sample size, blinding, independence, outcomes

### For a Claim
1. Identify the claim type: factual, causal, mechanistic, statistical, anecdotal
2. Find the primary source (PMID, NCT ID, company assertion)
3. Assess evidence level: established → supported → preliminary → unsubstantiated
4. Check for independent replication
5. Check for conflicts of interest

## Evidence Assessment Framework

| Level | Criteria | Example |
|-------|----------|---------|
| **Established** | Multiple large RCTs, meta-analyses, FDA-approved | G-CSF for stem cell mobilization |
| **Supported** | Small RCTs with replication, consistent preclinical | Exercise increases circulating progenitors |
| **Preliminary** | Single small trial, commercially-affiliated | SBB-PE mobilization (n=12, Drapeau/Jensen) |
| **Speculative** | Mechanistically plausible, no human data | Oral fucoidan mobilizes stem cells |
| **Unsubstantiated** | No supporting evidence or logical leap | Multi-ingredient supplement cures disease |

## Conflict of Interest Checklist

For every study, assess:
- [ ] Is the lead author affiliated with the product company?
- [ ] Is the testing lab a contract research org paid by the company?
- [ ] Is the study funded by the company?
- [ ] Has the finding been independently replicated?
- [ ] Are results published in a reputable (non-predatory) journal?

## Output Standards

All research output goes into the Obsidian vault (see `obsidian-vault-research` skill):
- Raw captures → `01-sources/raw-json/` and `01-sources/markdown/`
- Working analysis → `02-research/`
- Entity notes → `04-entities/`
- Synthesis → `03-syntheses/`

Always include:
- PMIDs, DOIs, NCT IDs, URLs for every claim
- `[UNVERIFIED]` markers for unconfirmed information
- Evidence quality ratings
- Conflict of interest assessments
- Explicit knowledge gaps and next steps

## Parallelization Strategy

For a full entity deep dive, launch parallel subagents:

```
Agent 1: Company fundamentals (Edgar + web search)
Agent 2: Person profile (PubMed + web search)
Agent 3: Website scraping (Firecrawl — all product pages)
Agent 4: Trial analysis (ClinicalTrials.gov + PubMed)
Agent 5: Compound research (PubChem + PubMed)
```

Collect results, then write vault notes sequentially to avoid conflicts.
