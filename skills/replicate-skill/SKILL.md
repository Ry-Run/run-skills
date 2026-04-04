---
name: replicate-skill
description: "Use Replicate MCP for models, predictions, trainings, deployments, and file management on Replicate. Use it when you need hosted AI workflows on Replicate, rather than general web research or local model execution."
---

# Replicate Skill

## Quick start

Goal: operate on Replicate resources directly: models, predictions, trainings, files, and deployments.

Reference notes: `skills/replicate-skill/references/replicate-skill.md`

## Common workflows

- Account and discovery: `get_account`, `search_models`, `list_models`, `get_models`, `get_models_readme`
- Run inference: `create_predictions` or `create_models_predictions`
- Poll jobs: `get_predictions`, `get_trainings`
- Manage training: `create_trainings`, `cancel_trainings`
- Manage deployments/files: `create_deployments`, `update_deployments`, `list_files`, `create_files`

## Recommended workflow

1. Inspect the model or version schema first.
2. For short jobs, use `Prefer: wait` when appropriate.
3. For long jobs, create then poll until terminal status.
4. Save or download outputs you need; hosted outputs may be removed later.

## High-risk actions

Require explicit confirmation before:
- deleting models, versions, deployments, or files
- canceling active predictions/trainings on behalf of the user
- changing live deployment configuration

## References

- Condensed notes: `skills/replicate-skill/references/replicate-skill.md`
