---
name: playwright-skill
description: 使用 Playwright MCP 做确定性的浏览器自动化：页面导航、表单填写、用户流程复现和轻量端到端交互。适合脚本化跨浏览器执行比 DevTools 级调试更重要的场景。
---

# Playwright Skill

## 快速上手

目标：在受控浏览器会话里复现用户流程，并能回看过程中发生了什么。

参考资料：`skills/playwright-skill/references/playwright-skill_zh.md`

## 最适合的场景

- 表单填写、登录、上传、多步骤流程。
- 按步骤复现 UI Bug。
- 需要确定性操作的浏览器检查。
- 轻量 E2E 验证与截图。

## 推荐工作流

1. 先导航到目标页面。
2. 交互前先抓一份快照。
3. 基于快照里的引用执行 click / type / fill / select。
4. 页面状态变化时，显式等待文本出现、消失或时间经过。
5. 如果流程失败，再查 console 或 network。

## 何时优先它

- 任务核心是执行用户动作。
- 你要的是稳定复现，而不是 DevTools 深度分析。
- 需要围绕一个脚本化流程做轻量网络 / 控制台检查。

## 约束与红线

- 交互前必须抓快照，不要用截图定位元素。
- `browser_run_code` 只在常规工具不够时再用。
- 涉及文件上传或可能改动真实数据的点击时，要视为高风险动作。

## 参考资料

- 摘录说明：`skills/playwright-skill/references/playwright-skill_zh.md`
