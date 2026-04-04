# Vercel MCP：摘录说明

## 核心工具分组

- 团队 / 项目发现：`list_teams`、`list_projects`、`get_project`
- 部署：`list_deployments`、`get_deployment`、`get_deployment_build_logs`、`deploy_to_vercel`
- 运行时日志：`get_runtime_logs`
- 受保护预览访问：`get_access_to_vercel_url`、`web_fetch_vercel_url`
- Toolbar 线程：`list_toolbar_threads`、`get_toolbar_thread`、`reply_to_toolbar_thread`、`change_toolbar_thread_resolve_status`
- 文档与域名：`search_vercel_documentation`、`check_domain_availability_and_price`

## 最适合的问题

- Vercel 部署排障
- 运行时错误排查
- 受鉴权保护的预览访问
- Vercel 平台文档查询

## 关键规则

- 先确定 `teamId` / `projectId`；很多时候 `.vercel/project.json` 是最快来源。
