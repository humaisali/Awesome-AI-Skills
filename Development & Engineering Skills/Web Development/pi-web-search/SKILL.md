---
name: pi-web-search
description: "Give Pi Agents a safe web-search and fetch workflow using the installed pi-web-access package."
category: research
risk: safe
source: https://github.com/humaisali
source_repo: davidondrej/skills
source_type: community
date_added: "2026-07-07"
Maintained & Curated by: Humais Ali
tags: [web-search, pi-agent, research]
tools: [claude, codex]
license: "MIT"
license_source: https://github.com/humaisali
---

# Web Search

## When to Use

- Use when a Pi Agent task needs current web information, page fetches, PDFs, YouTube, or GitHub content.
- Use when Pi should use its own web-access package instead of another agent browser tool.

The `pi-web-access` package is installed globally. Zero-config via Exa MCP (no API key), with fallback Exa â†’ Perplexity â†’ Gemini.

## CRITICAL: always pass `workflow: "none"`

Every `web_search` call MUST include `workflow: "none"`. This skips the interactive browser curator popup (the user does not want it opening). No exceptions â€” single query or batched `queries`, always set `workflow: "none"`.

```
web_search({ queries: ["query 1", "query 2"], workflow: "none" })
```

## Tools

- `web_search` â€” search the web; returns synthesized answers with citations. Can be called many times per turn. **Always pass `workflow: "none"`.**
- `code_search` â€” zero-key Exa code-context. Use for library/API/code lookups instead of generic `web_search`.
- `fetch_content` â€” fetch URL(s) â†’ markdown; handles PDFs, YouTube, GitHub.
- `get_search_content` â€” big pages (>30k chars) are truncated in responses but stored in full; call this to pull the rest on demand so they don't blow context.

## fetch_content specifics

- **GitHub URLs are cloned, not scraped** â€” you get real files + a local path to explore with `read`/`bash` (private repos need the `gh` CLI). Use this for dev work.
- **PDFs** â†’ auto-extracted to markdown in `~/Downloads/`, readable in sections (text-only, no OCR).
- **YouTube/video** â†’ full raw transcripts + frame extraction. Needs a `GEMINI_API_KEY` (not zero-config); frame extraction also needs `ffmpeg`/`yt-dlp`.

## Routing â€” match the user's phrasing

Always use the `web_search` tool. These counts are HARD MINIMUMS â€” count your queries before answering and do not stop short:

- **"web search"** â†’ **at least 2** queries, varied keywords/angles, then synthesize.
- **"extensive web research"** â†’ **at least 4** queries, totally different keywords and angles.
- **"deep research"** â†’ **at least 8** queries, totally different keywords and angles, run across 2â€“3 successive batches (refine angles after each batch), to learn as much as possible about the topic.

A single batched `web_search` call counts each query in `queries[]` toward the total. If your first batch is under the minimum, fire another batch before synthesizing.

## Fallback / alternative: DeepAPI web search

If the Exa â†’ Perplexity â†’ Gemini chain fails, or you need ranked results with URLs:

```bash
test -n "$DEEPAPI_API_KEY" || { echo "DEEPAPI_API_KEY is not set"; exit 1; }
curl -s --max-time 60 "https://deepapi.co/v1/search/web" \
  -H "Authorization: Bearer $DEEPAPI_API_KEY" -H "Content-Type: application/json" \
  -H "Idempotency-Key: $(uuidgen)" \
  -d '{"query": "your search terms", "maxResults": 5, "maxCostUsd": "0.05"}'
```

Results are in `.output` (title, url, snippet per item). Query under 500 chars. Full details: `deepapi` skill.

## Limitations

- Adapted from `davidondrej/skills`; verify local paths, tools, credentials, and agent features before acting.
- For commands, remote access, scheduling, browser automation, or file-changing workflows, get explicit user approval and confirm the target environment first.

