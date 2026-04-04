---
name: deepwiki
description: 使用 DeepWiki MCP 拉取 deepwiki.com 上的仓库级文档。适合快速理解外部仓库的架构概览、目录结构与仓库概念，而不是查实时库文档或做宽泛网页研究。
---

# DeepWiki Skill

## 快速上手

目标：在阅读外部仓库源码之前，先用 DeepWiki 快速拿到项目级文档概览。

主入口：
- `mcp__mcp_deepwiki__deepwiki_fetch`

参考资料：`skills/deepwiki/references/deepwiki_zh.md`

## 适用场景

- 需要快速了解外部仓库架构。
- 想先读仓库级文档，再决定是否深入源码。
- 需要 API、结构或核心概念摘要。

## 推荐工作流

1. 传入 `owner/repo`、仓库 URL 或库关键字。
2. 只看单页时用 `maxDepth: 0`，想稍微展开再用 `maxDepth: 1`。
3. 阅读返回的 Markdown。
4. 如果还不够，再切换到源码或官方文档。

## 约束与红线

- 先从小范围抓取开始，不要一上来就扩大深度。
- DeepWiki 更适合做二手结构化摘要，不保证覆盖最新未发布改动。
- 高准确性场景，仍要回源仓库或官方文档核对。

## 参考资料

- 摘录说明：`skills/deepwiki/references/deepwiki_zh.md`
