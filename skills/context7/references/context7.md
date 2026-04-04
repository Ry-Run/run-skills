# Context7 MCP: notes (condensed)

Use this reference to confirm the two-step workflow.

## Tools

- `mcp__context7__resolve_library_id`
  - Input: `libraryName`, `query`
  - Output: matching libraries with ID, description, snippet count, reputation, versions

- `mcp__context7__query_docs`
  - Input: `libraryId`, `query`
  - Output: current docs + examples for the chosen library

## Required pattern

1. Resolve the library ID first.
2. Choose the best match.
3. Query docs with a concrete technical question.

Exception:
- If the user already provided a Context7-style ID such as `/vercel/next.js` or `/org/project/version`, you may query directly.

## Best-fit use cases

- API usage
- Setup and configuration
- Version migrations
- Integration examples

## Limits

- Do not call Context7 more than 3 times per question.
