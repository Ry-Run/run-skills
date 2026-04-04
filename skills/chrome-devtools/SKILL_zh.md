---
name: chrome-devtools
description: 使用 Chrome DevTools MCP 做真实浏览器调试：控制台与网络检查、运行时状态分析、Lighthouse 审计和性能追踪。适合更关心诊断问题和浏览器内部状态，而不是脚本化跨浏览器自动化的场景。
---

# Chrome DevTools Skill

## 快速上手

目标：用 DevTools 风格工具直接调试真实页面，包括快照、控制台、网络、截图、审计和性能追踪。

参考资料：`skills/chrome-devtools/references/chrome-devtools_zh.md`

## 最适合的场景

- 真实浏览器里的前端调试。
- 检查控制台报错、网络请求、运行时状态。
- 跑 Lighthouse 或性能追踪。
- 页面交互依赖真实 DOM 状态时。

## 推荐工作流

1. 打开或选中目标页面。
2. 交互前先取一份可访问性快照。
3. 确认元素 UID 后再 click / fill / type。
4. 行为不清楚时先查 console / network。
5. 做质量或性能任务时再调用 Lighthouse / trace。

## 何时优先它

- 需要控制台、网络、trace、审计能力。
- 需要直接在当前页面执行 DOM 级脚本。
- 任务是“调试 web app”，而不仅仅是“复现操作流程”。

## 约束与红线

- 点击或输入前，必须基于最新快照。
- PDF 截图优先按页处理。
- 性能追踪比普通检查更重，只在需要时开启。

## 参考资料

- 摘录说明：`skills/chrome-devtools/references/chrome-devtools_zh.md`
