# Vercel MCP: notes (condensed)

## Core tool groups

- Team/project discovery: `list_teams`, `list_projects`, `get_project`
- Deployments: `list_deployments`, `get_deployment`, `get_deployment_build_logs`, `deploy_to_vercel`
- Runtime logs: `get_runtime_logs`
- Protected preview access: `get_access_to_vercel_url`, `web_fetch_vercel_url`
- Toolbar threads: `list_toolbar_threads`, `get_toolbar_thread`, `reply_to_toolbar_thread`, `change_toolbar_thread_resolve_status`
- Docs and domain checks: `search_vercel_documentation`, `check_domain_availability_and_price`

## Best-fit use cases

- Vercel deployment debugging
- Runtime error investigation
- Preview access behind auth
- Vercel-specific docs lookup

## Key rule

- Resolve `teamId` / `projectId` first; `.vercel/project.json` is often the fastest source.
