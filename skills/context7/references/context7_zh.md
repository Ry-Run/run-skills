# Context7 MCP：摘录说明

这个参考文档用于确认 Context7 的两步工作流。

## 工具

- `mcp__context7__resolve_library_id`
  - 输入：`libraryName`、`query`
  - 输出：候选库列表，包含 ID、简介、示例数量、信誉、版本

- `mcp__context7__query_docs`
  - 输入：`libraryId`、`query`
  - 输出：该库当前文档与代码示例

## 固定模式

1. 先解析 library ID。
2. 选择最匹配项。
3. 再针对具体技术问题查文档。

例外：
- 如果用户已经给了 `/vercel/next.js` 或 `/org/project/version` 这类 Context7 ID，可以直接查询。

## 最适合的问题

- API 用法
- 初始化与配置
- 版本迁移
- 集成示例

## 限制

- 同一个问题中，Context7 调用次数不要超过 3 次。
