---
name: vercel-skill
description: 使用 Vercel MCP 处理项目发现、部署、构建与运行日志、Toolbar 线程、受保护预览访问和 Vercel 文档。适合任务核心在 Vercel 托管应用状态上，而不是本地执行时使用。
---

# Vercel Skill

## 快速上手

目标：直接检查和操作真实的 Vercel 项目、部署、日志与反馈线程。

参考资料：`skills/vercel-skill/references/vercel-skill_zh.md`

## 常用流程

- 发现身份：`list_teams`、`list_projects`、`get_project`
- 部署状态：`list_deployments`、`get_deployment`、`get_deployment_build_logs`
- 运行时行为：`get_runtime_logs`
- 受保护预览：`get_access_to_vercel_url`、`web_fetch_vercel_url`
- 协作反馈：`list_toolbar_threads`、`get_toolbar_thread`、`reply_to_toolbar_thread`
- 文档：`search_vercel_documentation`

## 推荐工作流

1. 先解析 `teamId` 和 `projectId`；有 `.vercel/project.json` 就优先用它。
2. 先读 deployment / build / runtime 状态，再决定动作。
3. 预览页被 Vercel 鉴权保护时，用专门的 URL 工具，不要硬抓。
4. 涉及平台行为时，先搜 Vercel 官方文档，不要猜。

## 高风险动作

以下操作前必须明确确认：
- 触发部署到 Vercel
- 替用户编辑或解决 Toolbar 线程
- 仅凭局部日志就变更关键项目流程

## 参考资料

- 摘录说明：`skills/vercel-skill/references/vercel-skill_zh.md`
