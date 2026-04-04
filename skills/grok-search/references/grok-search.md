# Grok Search MCP: notes (condensed)

## Planning phases

1. `plan_intent`
2. `plan_complexity`
3. `plan_sub_query`
4. `plan_search_term`
5. `plan_tool_mapping`
6. `plan_execution`

## Execution tools

- `web_search`: answer-oriented search with optional extra sources
- `web_fetch`: fetch and extract full page content
- `web_map`: crawl site structure from a root URL
- `get_sources`: inspect sources from a prior search session

## Key rule

- Begin with planning; complexity level determines how many phases are required.
