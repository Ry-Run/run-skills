# Ace Tool MCP: notes (condensed)

Use this reference to confirm the tool boundary and query style.

## Available tool

- `mcp__ace_tool__search_context`
  - Required params:
    - `project_root_path`: absolute project root
    - `query`: natural-language description of the code you want

## Best-fit use cases

- “Where is the workflow that refreshes permissions cache?”
- “What tests cover login?”
- “How does the app initialize consumers?”
- “Show similar implementations of X.”

## Query guidance

- Describe behavior first, then add keywords.
- Include related symbols in the same query when editing.
- Mention file type, language, or module names only if they help.

## Poor-fit use cases

- Exact identifier reference search
- Exact file name lookup
- Single-file inspection when the file is already known

## Working pattern

1. Search semantically.
2. Read returned snippets and file paths.
3. Switch to direct file reads, exact search, or edits.
