---
name: "research-summarizer"
description: "Structured research summarization agent skill for non-dev users. Handles academic papers, web articles, reports, and documentation. Extracts key findings, generates comparative analyses, and produces properly formatted citations. Use when: user wants to summarize a research paper, compare multiple sources, extract citations from documents, or create structured research briefs. Plugin for Claude Code, Codex, Gemini CLI, and OpenClaw."
license: MIT
metadata:
  version: 1.0.0
  Maintained & Curated by: Humais Ali
  category: product
  updated: 2026-03-16
---

# Research Summarizer

> Read less. Understand more. Cite correctly.

Structured research summarization workflow that turns dense source material into actionable briefs. Built for product managers, analysts, founders, and anyone who reads more than they should have to.

Not a generic "summarize this" â€” a repeatable framework that extracts what matters, compares across sources, and formats citations properly.

---

## Scope â€” Distinct From the research/ Domain

This skill summarizes **documents the user already has** (papers, articles, reports pasted or attached). It performs no web search and needs no MCP server. It is NOT:

- `research/litreview` â€” academic literature *discovery* and review-guide generation (finds papers via Consensus/academic APIs)
- `research/dossier` â€” entity due-diligence built from live web research
- `research/notebooklm` â€” drives Google's NotebookLM product UI
- `research/research` â€” the router for open-ended "research [topic]" requests that require searching

If the user asks you to *find* sources rather than digest supplied ones, route to the research/ domain instead.

---

## When This Skill Activates

Recognize these patterns from the user:

- "Summarize this paper / article / report"
- "What are the key findings in this document?"
- "Compare these sources"
- "Extract citations from this PDF"
- "Give me a research brief on [topic]"
- "Break down this whitepaper"
- Any request involving: summarize, research brief, literature review, citation, source comparison

If the user has a document and wants structured understanding â†’ this skill applies.

---

## Workflow

### Workflow 1 â€” Single Source Summary

1. **Identify source type**
   - Academic paper â†’ use IMRAD structure (Introduction, Methods, Results, Analysis, Discussion)
   - Web article â†’ use claim-evidence-implication structure
   - Technical report â†’ use executive summary structure
   - Documentation â†’ use reference summary structure

2. **Scaffold the brief** â€” `python3 scripts/format_summary.py --template academic` (or `article`/`report`/`executive` per source type), then fill in every section from the source:
   ```
   Title: [exact title]
   Author(s): [names]
   Date: [publication date]
   Source Type: [paper | article | report | documentation]

   ## Key Thesis
   [1-2 sentences: the central argument or finding]

   ## Key Findings
   1. [Finding with supporting evidence]
   2. [Finding with supporting evidence]
   3. [Finding with supporting evidence]

   ## Methodology
   [How they arrived at these findings â€” data sources, sample size, approach]

   ## Limitations
   - [What the source doesn't cover or gets wrong]

   ## Actionable Takeaways
   - [What to do with this information]

   ## Notable Quotes
   > "[Direct quote]" (p. X)
   ```

3. **Assess quality**
   - Source credibility (peer-reviewed, reputable outlet, primary vs secondary)
   - Evidence strength (data-backed, anecdotal, theoretical)
   - Recency (when published, still relevant?)
   - Bias indicators (funding source, author affiliation, methodology gaps)

### Workflow 2 â€” Multi-Source Comparison

1. **Collect sources** (2-5 documents)
2. **Summarize each** using the single-source workflow above
3. **Build comparison matrix**

   ```
   | Dimension        | Source A        | Source B        | Source C        |
   |------------------|-----------------|-----------------|-----------------|
   | Central Thesis   | ...             | ...             | ...             |
   | Methodology      | ...             | ...             | ...             |
   | Key Finding      | ...             | ...             | ...             |
   | Sample/Scope     | ...             | ...             | ...             |
   | Credibility      | High/Med/Low    | High/Med/Low    | High/Med/Low    |
   ```

4. **Synthesize**
   - Where do sources agree? (convergent findings = stronger signal)
   - Where do they disagree? (divergent findings = needs investigation)
   - What gaps exist across all sources?
   - What's the weight of evidence for each position?

5. **Produce synthesis brief**
   ```
   ## Consensus Findings
   [What most sources agree on]

   ## Contested Points
   [Where sources disagree, with strongest evidence for each side]

   ## Gaps
   [What none of the sources address]

   ## Recommendation
   [Based on weight of evidence, what should the reader believe/do?]
   ```

### Workflow 3 â€” Citation Extraction

1. **Run the extractor** â€” `python3 scripts/extract_citations.py document.txt --output json` detects DOI/URL/author-year/numbered citations and deduplicates them
2. **Review and format** the extracted list in the requested style (APA 7 default); manually catch citations the regex missed
3. **Classify citations** by type:
   - Primary sources (original research, data)
   - Secondary sources (reviews, meta-analyses, commentary)
   - Tertiary sources (textbooks, encyclopedias)
4. **Output** sorted bibliography with classification tags

Supported citation formats:
- **APA 7** (default) â€” social sciences, business
- **IEEE** â€” engineering, computer science
- **Chicago** â€” humanities, history
- **Harvard** â€” general academic
- **MLA 9** â€” arts, humanities

---

## Tooling

### `scripts/extract_citations.py`

CLI utility for extracting and formatting citations from text.

**Features:**
- Regex-based citation detection (DOI, URL, author-year, numbered references)
- Multiple output formats (APA, IEEE, Chicago, Harvard, MLA)
- JSON export for integration with reference managers
- Deduplication of repeated citations

**Usage:**
```bash
# Extract citations from a file (APA format, default)
python3 scripts/extract_citations.py document.txt

# Specify format
python3 scripts/extract_citations.py document.txt --format ieee

# JSON output
python3 scripts/extract_citations.py document.txt --format apa --output json

# From stdin
cat paper.txt | python3 scripts/extract_citations.py --stdin
```

### `scripts/format_summary.py`

CLI utility that emits **blank structured summary scaffolds** â€” you (the model) fill them in from the source. It does not analyze content itself.

**Features:**
- 6 templates: academic, article, report, executive, comparison, literature
- Configurable scaffold depth (brief, standard, detailed)
- Text and JSON output for downstream tooling

**Usage:**
```bash
# Generate structured summary template
python3 scripts/format_summary.py --template academic

# Brief executive summary format
python3 scripts/format_summary.py --template executive --length brief

# All templates listed
python3 scripts/format_summary.py --list-templates

# JSON output
python3 scripts/format_summary.py --template article --output json
```

---

## Quality Assessment Framework

Rate every source on four dimensions:

| Dimension | High | Medium | Low |
|-----------|------|--------|-----|
| **Credibility** | Peer-reviewed, established author | Reputable outlet, known author | Blog, unknown author, no review |
| **Evidence** | Large sample, rigorous method | Moderate data, sound approach | Anecdotal, no data, opinion |
| **Recency** | Published within 2 years | 2-5 years old | 5+ years, may be outdated |
| **Objectivity** | No conflicts, balanced view | Minor affiliations disclosed | Funded by interested party, one-sided |

**Overall Rating:**
- 4 Highs = Strong source â€” cite with confidence
- 2+ Mediums = Adequate source â€” cite with caveats
- 2+ Lows = Weak source â€” verify independently before citing

---

## Summary Templates

See `references/summary-templates.md` for:
- Academic paper summary template (IMRAD)
- Web article summary template (claim-evidence-implication)
- Technical report template (executive summary)
- Comparative analysis template (matrix + synthesis)
- Literature review template (thematic organization)

See `references/citation-formats.md` for:
- APA 7 formatting rules and examples
- IEEE formatting rules and examples
- Chicago, Harvard, MLA quick reference

---

## Proactive Triggers

Flag these without being asked:

- **Source has no date** â†’ Note it. Undated sources lose credibility points.
- **Source contradicts other sources** â†’ Highlight the contradiction explicitly. Don't paper over disagreements.
- **Source is behind a paywall** â†’ Note limited access. Suggest alternatives if known.
- **User provides only one source for a compare** â†’ Ask for at least one more. Comparison needs 2+.
- **Citations are incomplete** â†’ Flag missing fields (year, author, title). Don't invent metadata.
- **Source is 5+ years old in a fast-moving field** â†’ Warn about potential obsolescence.

---

## Installation

### One-liner (any tool)
```bash
git clone https://github.com/alirezarezvani/claude-skills.git
cp -r claude-skills/product-team/research-summarizer ~/.claude/skills/
```

### Multi-tool install (run from the claude-skills repo root)
```bash
./scripts/convert.sh --skill research-summarizer --tool codex|gemini|cursor|windsurf|openclaw
```

### OpenClaw
```bash
clawhub install cs-research-summarizer
```

---

## Verification Loop

Before delivering any brief, check:

1. Every Key Finding cites a location in the source (section, page, or quote) â€” no unanchored claims.
2. `python3 scripts/extract_citations.py <file> --output json` exits 0 and its `total` matches the bibliography count in your output (investigate any gap).
3. Each source carries a 4-dimension quality rating (table above); weak sources are flagged, not silently included.
4. For comparisons: the matrix has one row per dimension and one column per source â€” no source skipped.
5. Nothing was invented: missing metadata is marked "not stated", never filled in.

---

## Related Skills

- **product-analytics** â€” Quantitative analysis. Complementary â€” use research-summarizer for qualitative sources, product-analytics for metrics.
- **competitive-teardown** â€” Competitive research. Complementary â€” use research-summarizer for individual source analysis, competitive-teardown for market landscape.
- **content-production** â€” Content writing. Research-summarizer feeds content-production â€” summarize sources first, then write.
- **product-discovery** â€” Discovery frameworks. Complementary â€” research-summarizer for desk research, product-discovery for user research.

