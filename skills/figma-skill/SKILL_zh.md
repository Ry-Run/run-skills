---
name: figma-skill
description: 使用 Figma MCP 完成 design-to-code、code-to-Figma、设计系统检索、Code Connect 与直接写入 Figma 画布。适合需要真实 Figma 文件上下文或要修改 Figma 文档的场景，而不是通用浏览器自动化。
---

# Figma Skill

## 快速上手

目标：直接基于真实 Figma 文件工作，而不是根据截图或模糊描述去猜。

参考资料：`skills/figma-skill/references/figma-skill_zh.md`

## 默认工具选择

- 理解设计：`get_design_context`
- 只看结构：`get_metadata`
- 截图：`get_screenshot`
- 设计系统检索：`search_design_system`
- 直接写画布：`use_figma`
- 首次把网页抓进 Figma：`generate_figma_design`

## 推荐工作流

1. 从 Figma URL 提取 `fileKey` 和 `nodeId`。
2. design-to-code 默认先用 `get_design_context`。
3. 创建组件前，先搜设计系统有没有现成资产。
4. 修改现有文件时，用 `use_figma`。
5. `generate_figma_design` 只用于“第一次把网页 / 页面抓进 Figma”。

## Code Connect 工作流

- 读映射：`get_code_connect_map`
- 拿建议：`get_code_connect_suggestions`
- 保存确认后的映射：`send_code_connect_mappings`
- 直接补单条映射：`add_code_connect_map`

## 约束与红线

- 只要需要真实实现上下文，就优先 `get_design_context`，不要只看 `get_metadata`。
- 重新造组件前先搜设计系统。
- 大范围删除 / 重写画布属于高风险操作，先确认再做。

## 参考资料

- 摘录说明：`skills/figma-skill/references/figma-skill_zh.md`
