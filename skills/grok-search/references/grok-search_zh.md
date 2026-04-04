# Grok Search MCP：摘录说明

## 规划阶段

1. `plan_intent`
2. `plan_complexity`
3. `plan_sub_query`
4. `plan_search_term`
5. `plan_tool_mapping`
6. `plan_execution`

## 执行工具

- `web_search`：以回答为中心的搜索，可附加额外来源
- `web_fetch`：抓取并提取完整页面内容
- `web_map`：从根 URL 开始爬取站点结构
- `get_sources`：查看已有搜索会话的来源

## 关键规则

- 先规划再执行；复杂度等级决定必须走完多少阶段。
