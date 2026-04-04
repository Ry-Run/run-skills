---
name: context7
description: 使用 Context7 MCP 获取绑定精确 library ID 的最新库/框架文档与示例代码。适合版本化 API 用法、setup、迁移与示例，而不是泛化文档站搜索。
---

# Context7 Skill

## 快速上手

目标：遇到库、框架、SDK 的问题时，直接查当前文档，而不是凭记忆回答。

标准流程：
1. `mcp__context7__resolve_library_id`
2. `mcp__context7__query_docs`

参考资料：`skills/context7/references/context7_zh.md`

## 适用场景

- 库 / 框架用法问题。
- 初始化、迁移、升级、集成接入。
- 某个版本下的 API 行为。
- 需要当前官方示例代码。

## 推荐工作流

1. 先把包名 / 产品名解析成精确的 Context7 library ID。
2. 根据名称、示例覆盖度、来源信誉选择最匹配的一项。
3. 用聚焦的问题查询文档。
4. 如需换角度再查一次，但整题尽量不要超过 3 次调用。

## 查询写法

- 明确语言 / 框架与具体目标。
- 用户给了版本，就把版本带上。
- 问题要具体：认证、路由、部署、schema、hooks、缓存等。

## 约束与红线

- 除非用户已经给出 `/org/project` 或 `/org/project/version`，否则先 `resolve_library_id`，再 `query_docs`。
- 单个问题内，Context7 总调用尽量控制在 3 次以内。
- 遇到库文档问题，优先用 Context7，而不是泛化网页搜索。

## 参考资料

- 摘录说明：`skills/context7/references/context7_zh.md`
