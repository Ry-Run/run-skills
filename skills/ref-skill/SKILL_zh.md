---
name: ref-skill
description: 使用 Ref MCP 先搜索文档源，再读取搜索结果中的精确 URL。适合先找对文档页、再读该页正文的场景，而不是基于精确 library ID 的版本化库文档查询。
---

# Ref Skill

## 快速上手

目标：先找文档页，再把那一页按 Markdown 读进来。

标准流程：
1. `mcp__Ref__ref_search_documentation`
2. `mcp__Ref__ref_read_url`

参考资料：`skills/ref-skill/references/ref-skill_zh.md`

## 适用场景

- 需要官方文档或 API 参考页。
- 想先拿到具体文档 URL，再读正文。
- 需要“文档搜索”，而不是泛化网页搜索。

## 推荐工作流

1. 查询里写清语言、框架或库名。
2. 选择最相关结果。
3. 用 `ref_read_url` 读取该结果返回的精确 URL。

## 约束与红线

- `ref_read_url` 只能读取搜索结果里返回的精确 URL。
- Ref 适合文档检索，不适合新闻、论坛、观点类搜索。
- 如果你需要的是最新事实而非文档正文，应切换到真正的网页搜索工具。

## 参考资料

- 摘录说明：`skills/ref-skill/references/ref-skill_zh.md`
