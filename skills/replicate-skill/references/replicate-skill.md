# Replicate MCP: notes (condensed)

## Major tool groups

- Account/discovery: `get_account`, `search_models`, `list_models`, `get_models`, `get_models_versions`
- Predictions: `create_predictions`, `create_models_predictions`, `get_predictions`, `list_predictions`, `cancel_predictions`
- Trainings: `create_trainings`, `get_trainings`, `list_trainings`, `cancel_trainings`
- Deployments: `create_deployments`, `get_deployments`, `update_deployments`, `list_deployments`, `delete_deployments`
- Files: `create_files`, `get_files`, `list_files`, `download_files`, `delete_files`

## Best-fit use cases

- Hosted model inspection
- Prediction execution
- Async training/prediction polling
- Deployment management

## Key rule

- Inspect the model/version schema before creating predictions or trainings.
