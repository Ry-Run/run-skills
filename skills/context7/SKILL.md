---
name: context7
description: "Use Context7 MCP for up-to-date library and framework documentation tied to an exact library ID. Use it for versioned API usage, setup, migrations, and code examples, rather than generic documentation-site search."
---

# Context7

## Quick start

Goal: fetch current documentation and code examples for a specific library or framework instead of relying on memory.

Core workflow:
1. `mcp__context7__resolve_library_id`
2. `mcp__context7__query_docs`

Reference notes: `skills/context7/references/context7.md`

## When to use it

- Library or framework usage questions.
- Setup, migration, upgrade, or integration guidance.
- Version-specific API behavior.
- Need current code examples from docs.

## Workflow

1. Resolve the package/product name to an exact Context7 library ID.
2. Pick the highest-quality match based on name, coverage, and source reputation.
3. Query docs with a focused technical question.
4. Re-query only if you need a different angle; avoid exceeding 3 calls per question.

## Query guidance

- Include the language/framework and concrete task.
- Mention the version when the user provides one.
- Ask for the exact thing you need: auth, routing, deployment, schema, hooks, etc.

## Guardrails

- Do not call `query_docs` before resolving the library ID unless the user already gave `/org/project` or `/org/project/version`.
- Keep to 3 Context7 calls or fewer per question.
- Prefer Context7 over generic web search for library docs.

## References

- Condensed notes: `skills/context7/references/context7.md`
