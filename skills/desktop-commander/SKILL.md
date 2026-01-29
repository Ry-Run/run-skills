---
name: desktop-commander-skill
description: 使用 Desktop Commander MCP（常见为 `mcp__desktop-commander__*` 工具）进行本地文件/目录读写与搜索、精确文本替换、Excel/PDF 处理、启动与交互长生命周期进程（Python/Node/SSH/DB）、查看与终止进程/会话、读取工具调用历史与用量统计、管理服务器配置。适用于：需要“在机器上执行操作”的任务（读写代码/配置、批量改文件、搜索代码、分析 CSV/Excel、生成/修改 PDF、跑命令并持续读取输出、交互式 REPL 调试/数据分析）时。
---

# Desktop Commander Skill

## 快速上手

目标：用 Desktop Commander Skill 把“文件/进程/搜索/编辑”变成可验证、可回放、可控风险的工具调用，而不是把整机当黑盒。

最常用的 4 个入口：
- 文件读取：优先 `mcp__desktop-commander__read_file`（支持分页、负 offset 类 tail、PDF/图片/Excel/URL）。
- 小范围改动：优先 `mcp__desktop-commander__edit_block`（文本精确替换/Excel 区域更新），避免整文件重写。
- 大范围改动：用 `mcp__desktop-commander__write_file` 分块写入（遵守 `fileWriteLineLimit`）。
- 长命令/交互：用 `mcp__desktop-commander__start_process` + `mcp__desktop-commander__interact_with_process` + `mcp__desktop-commander__read_process_output`。

更完整的工具清单与要点见：`skills/desktop-commander-mcp/references/desktop-commander-mcp-official.md`。

## 工作流决策树

1) 我需要“找东西”吗？
- 文件名/目录：`mcp__desktop-commander__start_search`（`searchType="files"`）→ `mcp__desktop-commander__get_more_search_results`
- 文件内容/代码关键字：`mcp__desktop-commander__start_search`（`searchType="content"`）→ 分页取结果 → 必要时 `mcp__desktop-commander__stop_search`

2) 我需要“读内容”还是“改内容”？
- 只读：`mcp__desktop-commander__read_file`（大文件用 `offset/length`；取末尾用 `offset=-N`）
- 小改动：`mcp__desktop-commander__edit_block`（默认只替换 1 处；多处用 `expected_replacements` 明确数量）
- 大改动：`mcp__desktop-commander__write_file`（`mode="rewrite"` + 后续 `mode="append"` 分块写）

3) 我需要“运行命令/维护会话”吗？
- 一次性命令（允许短输出即可）：用 `mcp__desktop-commander__start_process` 跑 `bash` 或具体命令
- 交互式 REPL/SSH/数据库/开发服务器：`start_process` 启动 → `interact_with_process` 发送输入 → `read_process_output` 拉取输出

4) 风险操作是否涉及：配置变更 / 终止进程 / 大批量改文件 / 删除数据？
- 先明确影响范围与回滚方案；需要用户明确确认后再执行。
- 配置变更优先在独立对话里做（官方文档强调这一点），避免“为了解决权限”而扩大访问范围。

## 常用配方

### 文件读取

- 读取文本/代码：用 `mcp__desktop-commander__read_file`，大文件用 `offset/length` 分页；看日志末尾用 `offset=-200`（类似 `tail`）。
- 读取多个文件：用 `mcp__desktop-commander__read_multiple_files`，比循环读取更省交互成本。
- 读 URL：`mcp__desktop-commander__read_file` 传 `isUrl: true`（适合把网页/图片抓进上下文做分析）。

### 文件编辑

- 精确替换（推荐）：用 `mcp__desktop-commander__edit_block`，把 `old_string/new_string` 写成最小可唯一匹配的上下文；多处替换务必设置 `expected_replacements`。
- 重写文件：用 `mcp__desktop-commander__write_file` 按 25–30 行分块，先 `mode="rewrite"`，再多次 `mode="append"`；避免一次性写超 `fileWriteLineLimit`。
- Excel：读取用 `read_file`，修改用 `edit_block` 的 `range` + 二维数组内容。
- PDF：创建/修改只用 `mcp__desktop-commander__write_pdf`（不要用 `write_file` 写 PDF）。

### 搜索

- 代码库探索优先 `mcp__desktop-commander__start_search`；需要分页/长搜索时配合 `get_more_search_results`，并在不需要后 `stop_search`。
- 想找文件名：`searchType="files"`；想找内容：`searchType="content"`；需要精确匹配特殊字符时把 `literalSearch` 设为 `true`。

### 进程与交互

- 数据分析（推荐）：`mcp__desktop-commander__start_process` 运行 `python3 -i` → `interact_with_process` 导入 pandas/numpy → 读文件 → 打印结果。
- 观察长任务：周期性调用 `mcp__desktop-commander__read_process_output` 拉新输出；卡住/需要停止时用 `mcp__desktop-commander__kill_process` 或 `mcp__desktop-commander__force_terminate`（高风险，先确认）。
- 排查状态：`mcp__desktop-commander__list_sessions` / `mcp__desktop-commander__list_processes`。

### 配置与审计

- `mcp__desktop-commander__get_config` / `mcp__desktop-commander__set_config_value`：谨慎使用；官方文档指出目录限制对“终端命令”不构成安全边界。
- `mcp__desktop-commander__get_recent_tool_calls`：恢复上下文、调试“我之前做了什么”。
- `mcp__desktop-commander__get_usage_stats`：了解使用情况与性能。

## 约束与红线（务必遵守）

- 路径：尽量使用绝对路径；涉及跨平台时不要假设分隔符或盘符。
- 大改动：先用 `read_file` 确认现状；改动尽量局部；写入必须分块并可回滚。
- 高风险操作（需要明确确认后才做）：修改配置、终止进程/会话、批量改动/移动文件、任何可能导致数据丢失的终端命令。
- 安全：官方文档明确说明 `allowedDirectories` 只限制文件工具，不限制终端命令；不要把它当“沙箱/隔离”。

## 参考资料

- 摘录与工具清单：`skills/desktop-commander-mcp/references/desktop-commander-skill.md`
