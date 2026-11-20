---
name: BulkPublish Social Publishing
description: Create, review, schedule, and publish approval-gated social media content through BulkPublish.
author: azeemkafridi
source: https://github.com/azeemkafridi/bulkpublish-api/tree/main/skills/social-media-content-skills
---

# BulkPublish Social Publishing

Use this skill when an AI agent needs to turn approved social content into scheduled or published posts across multiple social platforms.

## Required references

- BulkPublish API: https://github.com/azeemkafridi/bulkpublish-api
- BulkPublish MCP documentation: https://app.bulkpublish.com/docs
- Hosted MCP endpoint: https://mcp.bulkpublish.com/mcp

## Workflow

1. Confirm the content, destination platforms, account identifiers, media, links, timezone, and requested publish time.
2. Adapt the content to each platform while preserving the user's approved claims, links, disclosures, and brand constraints.
3. Present the complete per-platform payload and schedule summary for human approval.
4. Do not call a publish or schedule action until the user explicitly approves that exact payload and destination set.
5. Use BulkPublish's API or hosted MCP to create the approved post or schedule, then record the returned identifiers and status.
6. Verify the result by retrieving the post or schedule status; report failures per platform without silently retrying a potentially duplicated publish.

## Output

Return a concise table containing platform, account, status, scheduled time, post identifier, public URL when available, and any error or required follow-up.

## Safety checks

- Treat publishing as an external side effect requiring explicit, just-in-time approval.
- Never invent account IDs, media URLs, platform permissions, analytics, or delivery results.
- Preserve opt-outs, consent, copyright notes, and required platform disclosures.
- If BulkPublish reports an ambiguous timeout, check status before retrying.
