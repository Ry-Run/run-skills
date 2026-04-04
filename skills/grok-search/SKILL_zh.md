---
name: grok-search
description: 使用 Grok Search MCP 做“先规划、后执行”的网页研究：先定义意图、评估复杂度、拆分子问题，再执行搜索、抓取或站点映射。适合多来源、多子问题、需要显式研究计划的场景；如果已知当前使用的 Grok 模型，调用时应明确说明。
---

# Grok Search Skill

## 快速上手

目标：面对宽泛、分层、来源敏感的问题时，先做研究规划，而不是随手搜几下。

参考资料：`skills/grok-search/references/grok-search_zh.md`

## 必经规划流程

必须先从这里开始：
1. `mcp__grok_search__plan_intent`
2. `mcp__grok_search__plan_complexity`

然后按复杂度继续：
- Level 1：做到 sub-query 即可
- Level 2：继续补 search term 和 tool mapping
- Level 3：六个阶段全走完，包括执行顺序

执行工具：
- `mcp__grok_search__web_search`
- `mcp__grok_search__web_fetch`
- `mcp__grok_search__web_map`

## 适用场景

- 含多个子问题的研究任务。
- 需要显式规划信息来源与搜索顺序。
- 宽泛或歧义较强的网页调查。
- 需要站点结构映射或整页抓取。

## 推荐工作流

1. 先做研究规划。
2. 再执行对应的 search / fetch / map。
3. 如果要回溯来源，可对已有搜索会话调用 `get_sources`。

## 约束与红线

- 不能跳过 `plan_intent`。
- 如果知道当前使用的 Grok 模型，调用时必须显式说明。
- `web_fetch` 用来抓完整页面，不是用来搜索。
- `web_map` 用来看站点结构，不是直接生成答案。

## 参考资料

- 摘录说明：`skills/grok-search/references/grok-search_zh.md`
