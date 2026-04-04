---
name: vercel-skill
description: "Use Vercel MCP for project discovery, deployments, build and runtime logs, toolbar threads, protected preview access, and Vercel documentation. Use it when the task centers on Vercel-hosted application state, rather than local-only execution."
---

# Vercel Skill

## Quick start

Goal: inspect and operate on real Vercel projects, deployments, logs, and feedback threads.

Reference notes: `skills/vercel-skill/references/vercel-skill.md`

## Common workflows

- Discover identity: `list_teams`, `list_projects`, `get_project`
- Deployment status: `list_deployments`, `get_deployment`, `get_deployment_build_logs`
- Runtime behavior: `get_runtime_logs`
- Protected previews: `get_access_to_vercel_url`, `web_fetch_vercel_url`
- Collaboration: `list_toolbar_threads`, `get_toolbar_thread`, `reply_to_toolbar_thread`
- Docs: `search_vercel_documentation`

## Recommended workflow

1. Resolve `teamId` and `projectId` first. Use `.vercel/project.json` when present.
2. Read deployment/build/runtime state before taking action.
3. Use protected URL helpers when a preview is behind Vercel auth.
4. Search Vercel docs for platform-specific behavior instead of guessing.

## High-risk actions

Require explicit confirmation before:
- deploying to Vercel
- editing or resolving toolbar threads on behalf of the user
- changing project-critical workflows based only on partial logs

## References

- Condensed notes: `skills/vercel-skill/references/vercel-skill.md`
