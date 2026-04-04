---
name: deepwiki
description: "Use DeepWiki MCP for repository-focused documentation from deepwiki.com. Use it when you need a fast overview of an external repository, architecture, or repo-specific concepts, rather than live library docs or broad web research."
---

# DeepWiki

## Quick start

Goal: retrieve DeepWiki-generated repository documentation when you need a fast overview of an open source project.

Primary entry point:
- `mcp__mcp_deepwiki__deepwiki_fetch`

Reference notes: `skills/deepwiki/references/deepwiki.md`

## When to use it

- You need a quick architecture overview for an external repository.
- You want repo-level docs before reading raw source code.
- You need API, structure, or concept summaries from DeepWiki.

## Workflow

1. Pass an owner/repo, repo URL, or library keyword.
2. Use `maxDepth: 0` for one page/site, `maxDepth: 1` for broader coverage.
3. Read the returned markdown.
4. Switch to direct code or web docs only if DeepWiki is insufficient.

## Guardrails

- Prefer concise fetches first; widen depth only when needed.
- Treat DeepWiki as secondary documentation, not ground truth for latest unreleased changes.
- If accuracy is critical, verify against the real repository or official docs.

## References

- Condensed notes: `skills/deepwiki/references/deepwiki.md`
