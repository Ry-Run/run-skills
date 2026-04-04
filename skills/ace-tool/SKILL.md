---
name: ace-tool
description: "Use Ace Tool MCP (`mcp__ace_tool__search_context`) for semantic repository discovery. Use it when the exact file, symbol, or implementation path is unknown, rather than starting with exact IDE search or direct file edits."
---

# Ace Tool

## Quick start

Goal: use semantic repository search to answer “where is this implemented?” before falling back to exact text search or editing.

Primary entry point:
- `mcp__ace_tool__search_context`

Reference notes: `skills/ace-tool/references/ace-tool.md`

## When to use it

- You do not know which files contain the logic.
- You need cross-file context for a feature, bug, workflow, or subsystem.
- You want similar implementations or existing patterns before editing.
- You need a broad map of tests, handlers, services, or integration points.

## When not to use it

- Exact identifier lookup such as “find every `fooBar` reference”.
- Exact file name search.
- Small, already-known files where plain file reads are faster.

For exact string matching, switch to `rg`, IDE search, or other exact tools after semantic narrowing.

## Workflow

1. Write one natural-language query that describes the behavior, workflow, and important keywords.
2. Include all related symbols in the same query when planning an edit.
3. Read the returned file paths and snippets.
4. Follow up with exact reads or precise edits only after the location is clear.

## Query style

- Prefer behavior-first phrasing: “Where does the server merge upload chunks?”
- Add keywords at the end for recall.
- Ask about tests explicitly if you need them.
- Ask for multiple connected symbols in one query instead of many tiny queries.

## Guardrails

- Always pass the real project root path.
- Use Ace Tool before editing when file ownership is uncertain.
- Do not treat semantic matches as proof; verify with direct file reads.

## References

- Condensed notes: `skills/ace-tool/references/ace-tool.md`
