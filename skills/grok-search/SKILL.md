---
name: grok-search
description: "Use Grok Search MCP for planned web research: define intent, assess complexity, break the task into sub-queries, and then search, fetch, or map sources. Use it for multi-source research that benefits from explicit planning, and state which Grok model is being used whenever that is known."
---

# Grok Search

## Quick start

Goal: do deliberate web research instead of ad hoc searching when the question is broad, multi-part, or source-sensitive.

Reference notes: `skills/grok-search/references/grok-search.md`

## Required planning flow

Start with:
1. `mcp__grok_search__plan_intent`
2. `mcp__grok_search__plan_complexity`

Then continue based on complexity:
- Level 1: sub-queries only
- Level 2: add search terms and tool mapping
- Level 3: complete all phases including execution ordering

Execution tools:
- `mcp__grok_search__web_search`
- `mcp__grok_search__web_fetch`
- `mcp__grok_search__web_map`

## When to use it

- Research with multiple sub-questions.
- Tasks needing explicit source planning.
- Broad or ambiguous web investigations.
- Cases where site mapping or page fetching matters.

## Workflow

1. Plan the research.
2. Execute the right search/fetch/map actions.
3. If needed, inspect sources from a prior search with `get_sources`.

## Guardrails

- Do not skip `plan_intent`.
- State the Grok model explicitly when using this skill if the active model is known.
- Use `web_fetch` for full-page extraction, not search.
- Use `web_map` when you need site structure, not answer generation.

## References

- Condensed notes: `skills/grok-search/references/grok-search.md`
