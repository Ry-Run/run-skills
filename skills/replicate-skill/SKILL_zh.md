---
name: replicate-skill
description: 使用 Replicate MCP 直接操作 Replicate 上的模型、预测、训练、部署和文件。适合需要 Replicate 托管 AI 工作流的场景，而不是泛化网页研究或本地模型执行。
---

# Replicate Skill

## 快速上手

目标：直接操作 Replicate 资源，包括模型、预测、训练、文件和部署。

参考资料：`skills/replicate-skill/references/replicate-skill_zh.md`

## 常用流程

- 账户与发现：`get_account`、`search_models`、`list_models`、`get_models`、`get_models_readme`
- 跑推理：`create_predictions` 或 `create_models_predictions`
- 轮询任务：`get_predictions`、`get_trainings`
- 训练管理：`create_trainings`、`cancel_trainings`
- 部署 / 文件管理：`create_deployments`、`update_deployments`、`list_files`、`create_files`

## 推荐工作流

1. 先查看模型或版本 schema。
2. 短任务适合带 `Prefer: wait`。
3. 长任务则先创建，再轮询直到终态。
4. 需要的输出要及时保存或下载，因为托管输出后续可能被清理。

## 高风险动作

以下操作前必须明确确认：
- 删除模型、版本、部署或文件
- 替用户取消正在运行的 prediction / training
- 修改线上 deployment 配置

## 参考资料

- 摘录说明：`skills/replicate-skill/references/replicate-skill_zh.md`
