---
name: ref-skill
description: "Use Ref MCP to search documentation sources and then read the exact returned URL. Use it for documentation-site discovery and page-level reading when the right doc page is not yet known, rather than versioned library-ID lookup."
---

# Ref Skill

## Quick start

Goal: search for documentation pages and read the exact page content as markdown.

Core workflow:
1. `mcp__Ref__ref_search_documentation`
2. `mcp__Ref__ref_read_url`

Reference notes: `skills/ref-skill/references/ref-skill.md`

## When to use it

- You need official docs or API reference pages.
- You need direct documentation URLs before reading content.
- You want documentation search rather than generic web search.

## Workflow

1. Search with a query that names the language, framework, or library.
2. Pick the most relevant result.
3. Read the exact returned URL with `ref_read_url`.

## Guardrails

- `ref_read_url` should receive the exact URL from search results.
- Use Ref for documentation, not for general news or opinionated web search.
- If you need the latest facts outside docs, switch to a real web search tool.

## References

- Condensed notes: `skills/ref-skill/references/ref-skill.md`
