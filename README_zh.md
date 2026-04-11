<h1 align="center">Run Skills</h1>

<p align="center">
    <a href="./README.md">English</a> | <strong>简体中文</strong>
</p>

这是一个用于管理和分发 Gemini CLI 技能（Skills）的项目。每个技能都旨在增强模型在特定领域（如系统操作、代码分析等）的处理能力。

## 技能列表

| 技能名称                                               | 描述                                                         | 安装方法                                                     |
| :----------------------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| [ace-tool](skills/ace-tool/SKILL.md)                   | 使用 Ace Tool MCP 做语义代码搜索，在精确读取或编辑前快速定位工作流、模块、测试与相关实现。 | `npx skills add https://github.com/ry-run/run-skills --skill ace-tool` |
| [chrome-devtools](skills/chrome-devtools/SKILL.md)     | 使用 Chrome DevTools MCP 做真实浏览器调试、快照、控制台/网络检查、Lighthouse 审计与性能追踪。 | `npx skills add https://github.com/ry-run/run-skills --skill chrome-devtools` |
| [context7](skills/context7/SKILL.md)                   | 使用 Context7 MCP 获取当前库/框架文档，先解析 library ID，再做定向文档查询。 | `npx skills add https://github.com/ry-run/run-skills --skill context7` |
| [deepwiki](skills/deepwiki/SKILL.md)                   | 使用 DeepWiki MCP 快速获取开源仓库概览、架构说明与仓库级文档。 | `npx skills add https://github.com/ry-run/run-skills --skill deepwiki` |
| [desktop-commander](skills/desktop-commander/SKILL.md) | 使用 Desktop Commander MCP 进行本地文件/目录操作、精确文本替换、进程管理、搜索及 Excel/PDF 处理。 | `npx skills add https://github.com/ry-run/run-skills --skill desktop-commander` |
| [figma-skill](skills/figma-skill/SKILL.md)             | 使用 Figma MCP 读取与修改真实 Figma 文件，支持 design-to-code、设计系统搜索、截图与 Code Connect。 | `npx skills add https://github.com/ry-run/run-skills --skill figma-skill` |
| [frontend-dev-plain-web](skills/frontend-dev-plain-web/SKILL.md) | 以轻量流程开发纯 HTML/CSS/JS 网页，覆盖资料查证、本地实现、浏览器验证与定点调试。 | `npx skills add https://github.com/ry-run/run-skills --skill frontend-dev-plain-web` |
| [github-skill](skills/github-skill/SKILL.md)           | 使用 GitHub MCP 直接处理远端仓库、Issue、PR、Review、Release 与代码搜索。 | `npx skills add https://github.com/ry-run/run-skills --skill github-skill` |
| [grok-search](skills/grok-search/SKILL.md)             | 使用 Grok Search MCP 做先规划后执行的网页研究，适合多子问题和多来源检索。 | `npx skills add https://github.com/ry-run/run-skills --skill grok-search` |
| [jetbrains-skill](skills/jetbrains-skill/SKILL.md)     | 使用 JetBrains IDE MCP Server (IntelliJ 2025.2+) 驱动 IDE 动作：运行配置、终端命令、诊断、重构、索引搜索等。 | `npx skills add https://github.com/ry-run/run-skills --skill jetbrains-skill` |
| [playwright-skill](skills/playwright-skill/SKILL.md)   | 使用 Playwright MCP 做确定性的浏览器自动化，适合复现用户流程、表单交互和轻量 E2E 验证。 | `npx skills add https://github.com/ry-run/run-skills --skill playwright-skill` |
| [ref-skill](skills/ref-skill/SKILL.md)                 | 使用 Ref MCP 先搜文档再读精确 URL，适合官方文档、API 参考与文档站检索。 | `npx skills add https://github.com/ry-run/run-skills --skill ref-skill` |
| [replicate-skill](skills/replicate-skill/SKILL.md)     | 使用 Replicate MCP 处理模型、预测、训练、部署与文件等托管 AI 工作流。 | `npx skills add https://github.com/ry-run/run-skills --skill replicate-skill` |
| [sequential-thinking](skills/sequential-thinking/SKILL.md) | 使用 Sequential Thinking MCP 做显式分步、可修正、可分支的复杂推理与规划。 | `npx skills add https://github.com/ry-run/run-skills --skill sequential-thinking` |
| [shrimp-task-manager](skills/shrimp-task-manager/SKILL.md) | 使用 Shrimp Task Manager MCP 做结构化任务分析、拆解、执行指导与验收评分。 | `npx skills add https://github.com/ry-run/run-skills --skill shrimp-task-manager` |
| [vercel-skill](skills/vercel-skill/SKILL.md)           | 使用 Vercel MCP 处理项目、部署、日志、预览访问、Toolbar 线程与平台文档。 | `npx skills add https://github.com/ry-run/run-skills --skill vercel-skill` |

## 工作流推荐

### `frontend-dev-plain-web`

- 适合落地页、静态页、简单交互页这类纯 HTML/CSS/JS 页面开发。
- 主路径固定为：`context7` 查官方文档与 API，`ref-skill` 查 GitHub / issue / 实战代码，`grok-search` 查原理、对比、最佳实践、难查问题与所有非技术内容。
- 本地实现用 `desktop-commander`，主流程验证用 `playwright-skill`，只有需要深挖时再进入 `chrome-devtools`。
- 如果环境已安装，`frontend-design` 与 `uncodixfy` 用来提升页面结构与视觉质量；`adapt` 与 `polish` 保持可选。
- 使用 `grok-search` 时，如果知道当前 Grok 模型，必须显式说明。

## Skill 选择对照表

| 如果你现在要做的是… | 优先使用 | 不要先用 |
| :--- | :--- | :--- |
| 在真实浏览器里排查 console、network、性能问题 | `chrome-devtools` | `playwright-skill` |
| 稳定复现用户流程、填表单、执行浏览器交互 | `playwright-skill` | `chrome-devtools` |
| 查询某个已知库 / 框架的版本化文档 | `context7` | `ref-skill` |
| 先找文档页，再读取该页正文 | `ref-skill` | `context7` |
| 在不知道具体文件或符号时做语义找代码 | `ace-tool` | `jetbrains-skill` |
| 在已打开项目里做 IDE 索引、检查和安全重构 | `jetbrains-skill` | `ace-tool` |
| 把复杂分析或决策过程拆成显式推理步骤 | `sequential-thinking` | `shrimp-task-manager` |
| 管理带拆解、追踪和验收的任务系统 | `shrimp-task-manager` | `sequential-thinking` |
| 快速理解外部仓库的仓库级文档和结构概览 | `deepwiki` | `grok-search` |
| 对多个网页来源做有计划的研究 | `grok-search` | `deepwiki` |
| 直接处理本地文件、进程、PDF 或 Excel | `desktop-commander` | `github-skill`、`vercel-skill` |
| 从需求或参考资料开发纯 HTML/CSS/JS 网页 | `frontend-dev-plain-web` | 自己手动拼接整套流程 |
| 操作 GitHub 上的 PR、Issue、Review、Release 等远端状态 | `github-skill` | `desktop-commander` |
| 直接基于真实 Figma 文件、节点和设计系统工作 | `figma-skill` | `chrome-devtools`、`playwright-skill` |
| 检查 Vercel 上的部署、日志和预览状态 | `vercel-skill` | `desktop-commander` |
| 运行 Replicate 上的托管 AI 工作流 | `replicate-skill` | `grok-search` |
