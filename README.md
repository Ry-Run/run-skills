<h1 align="center">Run Skills</h1>

<p align="center">
    <strong>English</strong> | <a href="./README_zh.md">简体中文</a>
</p>

Run Skills is a project for managing and distributing Gemini CLI skills. Each skill is designed to enhance the model's capabilities in specific domains such as system operations, code analysis, and more.

## Skill List

| Name | Description | Installation |
| :--- | :--- | :--- |
| [ace-tool](skills/ace-tool/SKILL.md) | Semantic codebase search for locating workflows, modules, tests, and related implementation context before exact reads or edits. | `npx skills add https://github.com/ry-run/run-skills --skill ace-tool` |
| [chrome-devtools](skills/chrome-devtools/SKILL.md) | Browser-backed debugging with snapshots, console/network inspection, Lighthouse audits, and performance traces through Chrome DevTools MCP. | `npx skills add https://github.com/ry-run/run-skills --skill chrome-devtools` |
| [context7](skills/context7/SKILL.md) | Current library and framework documentation lookup with library ID resolution and targeted doc queries. | `npx skills add https://github.com/ry-run/run-skills --skill context7` |
| [deepwiki](skills/deepwiki/SKILL.md) | Quick repository documentation lookup from DeepWiki for open source project overviews and repo-level concepts. | `npx skills add https://github.com/ry-run/run-skills --skill deepwiki` |
| [desktop-commander](skills/desktop-commander/SKILL.md) | Local file/directory operations, precise text replacement, process management, search, and Excel/PDF processing via Desktop Commander MCP. | `npx skills add https://github.com/ry-run/run-skills --skill desktop-commander` |
| [figma-skill](skills/figma-skill/SKILL.md) | Real Figma file access for design-to-code, canvas edits, design system search, screenshots, Code Connect, and web capture. | `npx skills add https://github.com/ry-run/run-skills --skill figma-skill` |
| [frontend-dev-plain-web](skills/frontend-dev-plain-web/SKILL.md) | Lightweight workflow for building plain HTML/CSS/JS webpages from requirements with doc lookup, local implementation, browser verification, and focused debugging. | `npx skills add https://github.com/ry-run/run-skills --skill frontend-dev-plain-web` |
| [github-skill](skills/github-skill/SKILL.md) | Direct GitHub repository, issue, PR, review, release, and search operations against remote state. | `npx skills add https://github.com/ry-run/run-skills --skill github-skill` |
| [grok-search](skills/grok-search/SKILL.md) | Planned multi-phase web research with explicit intent, complexity, sub-query, and execution mapping. | `npx skills add https://github.com/ry-run/run-skills --skill grok-search` |
| [jetbrains-skill](skills/jetbrains-skill/SKILL.md) | Drive JetBrains IDE actions (IntelliJ 2025.2+): run configurations, terminal commands, diagnostics, refactoring, and indexed search. | `npx skills add https://github.com/ry-run/run-skills --skill jetbrains-skill` |
| [playwright-skill](skills/playwright-skill/SKILL.md) | Deterministic browser automation for reproducing user flows, interacting with forms, and capturing browser diagnostics. | `npx skills add https://github.com/ry-run/run-skills --skill playwright-skill` |
| [ref-skill](skills/ref-skill/SKILL.md) | Documentation-first search and page reading for official docs, API references, and connected documentation sources. | `npx skills add https://github.com/ry-run/run-skills --skill ref-skill` |
| [replicate-skill](skills/replicate-skill/SKILL.md) | Replicate model, prediction, training, deployment, and file workflows for hosted AI operations. | `npx skills add https://github.com/ry-run/run-skills --skill replicate-skill` |
| [sequential-thinking](skills/sequential-thinking/SKILL.md) | Explicit step-by-step reasoning support with revisions and branches for complex analysis and planning. | `npx skills add https://github.com/ry-run/run-skills --skill sequential-thinking` |
| [shrimp-task-manager](skills/shrimp-task-manager/SKILL.md) | Structured task analysis, decomposition, execution guidance, research tracking, and verification scoring. | `npx skills add https://github.com/ry-run/run-skills --skill shrimp-task-manager` |
| [vercel-skill](skills/vercel-skill/SKILL.md) | Vercel project, deployment, log, preview, toolbar thread, and documentation workflows. | `npx skills add https://github.com/ry-run/run-skills --skill vercel-skill` |

## Workflow Highlight

### `frontend-dev-plain-web`

- Use it for landing pages, static pages, and simple interactive pages that should stay in plain HTML, CSS, and JavaScript.
- Main path: `context7` for official docs, `ref-skill` for GitHub/issues/real-world code, `grok-search` for concepts, tradeoffs, best practices, hard-to-find questions, and non-technical research.
- Build locally with `desktop-commander`, verify with `playwright-skill`, and only step into `chrome-devtools` when you need deeper debugging.
- If installed, `frontend-design` and `uncodixfy` improve layout and visual quality; `adapt` and `polish` stay optional.
- When `grok-search` is used and the active Grok model is known, state that model explicitly.

## Skill Selection Guide

| If you need to... | Prefer | Instead of |
| :--- | :--- | :--- |
| Diagnose console errors, network failures, or performance issues in a real browser | `chrome-devtools` | `playwright-skill` |
| Reproduce user flows, fill forms, and run browser interactions deterministically | `playwright-skill` | `chrome-devtools` |
| Look up versioned docs for a known library or framework | `context7` | `ref-skill` |
| Search documentation sites first, then read the exact page | `ref-skill` | `context7` |
| Find code semantically when the exact file or symbol is unknown | `ace-tool` | `jetbrains-skill` |
| Use IDE indexing, inspections, and safe structural refactors in an open project | `jetbrains-skill` | `ace-tool` |
| Structure a difficult analysis or decision into explicit reasoning steps | `sequential-thinking` | `shrimp-task-manager` |
| Manage a task system with decomposition, tracking, and verification | `shrimp-task-manager` | `sequential-thinking` |
| Understand an external repository quickly from repo-level documentation | `deepwiki` | `grok-search` |
| Research across multiple web sources with an explicit search plan | `grok-search` | `deepwiki` |
| Work directly with local files, processes, PDFs, or Excel | `desktop-commander` | `github-skill`, `vercel-skill` |
| Build a plain HTML/CSS/JS webpage from requirements or references | `frontend-dev-plain-web` | stitching the workflow together manually |
| Operate on remote GitHub state such as PRs, issues, reviews, and releases | `github-skill` | `desktop-commander` |
| Work against real Figma files, nodes, and design systems | `figma-skill` | `chrome-devtools`, `playwright-skill` |
| Inspect deployments, logs, and preview state on Vercel | `vercel-skill` | `desktop-commander` |
| Run hosted AI workflows on Replicate | `replicate-skill` | `grok-search` |
