# Replicate MCP：摘录说明

## 主要工具分组

- 账户 / 发现：`get_account`、`search_models`、`list_models`、`get_models`、`get_models_versions`
- Prediction：`create_predictions`、`create_models_predictions`、`get_predictions`、`list_predictions`、`cancel_predictions`
- Training：`create_trainings`、`get_trainings`、`list_trainings`、`cancel_trainings`
- Deployment：`create_deployments`、`get_deployments`、`update_deployments`、`list_deployments`、`delete_deployments`
- 文件：`create_files`、`get_files`、`list_files`、`download_files`、`delete_files`

## 最适合的问题

- 托管模型检查
- 运行 prediction
- 轮询异步训练 / 推理任务
- 部署管理

## 关键规则

- 创建 prediction 或 training 前，先看模型 / 版本 schema。
