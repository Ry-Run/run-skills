# Desktop Commander MCP：摘录与整理

本文件的用途：
- 需要查“有哪些工具/每个工具干什么/关键限制”时再加载
- 不作为完整安装指南（安装/Remote MCP/Docker 细节可按需另查官方 README）

## 工具分类与清单（按官方 README）

说明：不同宿主会把工具暴露为短名（如 `read_file`），或带命名空间（如 `mcp__desktop-commander__read_file`）。本技能以带命名空间为主，短名可视为同名映射。

### Configuration
- `get_config`：获取服务端完整配置（JSON），包含 `blockedCommands`、`defaultShell`、`allowedDirectories`、`fileReadLineLimit`、`fileWriteLineLimit`、`telemetryEnabled` 等。
- `set_config_value`：设置单个配置项。

### Terminal
- `start_process`：启动程序/命令，并检测何时“可交互”。
- `interact_with_process`：向运行中的进程发送输入并获取响应（适合 REPL/SSH/数据库/开发服务器）。
- `read_process_output`：读取运行中进程的输出（支持分页 offset/length）。
- `force_terminate`：强制终止终端会话。
- `list_sessions`：列出所有活跃终端会话。
- `list_processes`：列出系统运行进程（含 CPU/内存等）。
- `kill_process`：按 PID 终止进程。

### Filesystem
- `read_file`：读取本地文件/URL/Excel/PDF；支持行/页分页；支持 `offset=-N` 从末尾读取。
- `read_multiple_files`：同时读取多个文件。
- `write_file`：写入文本或 Excel（JSON 二维数组）；支持 `mode="rewrite"`/`mode="append"`；PDF 请使用 `write_pdf`。
- `write_pdf`：用 markdown 创建新 PDF 或对现有 PDF 执行插入/删除页；支持 HTML/CSS 与 SVG。
- `create_directory`：创建目录（或确保存在）。
- `list_directory`：递归列出目录内容（`depth` 默认 2）。
- `move_file`：移动/重命名文件或目录。
- `start_search`：开始流式搜索（按文件名或内容；可搜索 Excel 内容）。
- `get_more_search_results`：对搜索结果做分页读取（offset/length）。
- `stop_search`：停止搜索。
- `list_searches`：列出当前活跃搜索会话。
- `get_file_info`：获取文件/目录元信息（Excel 会返回 sheet 信息等）。

### Text Editing
- `edit_block`：文本文件“精确替换”；Excel 文件“范围更新”（`range` + 二维数组）。

### Analytics
- `get_usage_stats`：统计信息。
- `get_recent_tool_calls`：最近工具调用历史（含参数/输出），用于调试与上下文恢复。
- `give_feedback_to_desktop_commander`：打开反馈表单。

## 关键限制与安全提醒

### `allowedDirectories` 的边界
明确：`allowedDirectories` 仅限制“文件类工具”的访问范围，不限制“终端命令”。终端命令仍可能访问该范围外的文件。

结论：不要把 `allowedDirectories` 当作安全沙箱；需要隔离时优先考虑 Docker 等真正隔离方案。

### 配置变更建议
建议：把配置变更放到独立对话里做，避免在“做事的对话”中为了绕过限制而扩大权限。

### `fileWriteLineLimit` 的意义
说明：`fileWriteLineLimit`（默认 50 行）是为了迫使 AI 做小步变更，减少 token 浪费，并降低“消息被截断导致改动丢失”的风险。该值可调大到上千，但不建议常态化这么做。

## 与本环境工具名的映射（常见）

如果宿主把工具暴露为命名空间形式，则通常是：
- `read_file` → `mcp__desktop-commander__read_file`
- `write_file` → `mcp__desktop-commander__write_file`
- `edit_block` → `mcp__desktop-commander__edit_block`
- `start_process` → `mcp__desktop-commander__start_process`
- `interact_with_process` → `mcp__desktop-commander__interact_with_process`
- `read_process_output` → `mcp__desktop-commander__read_process_output`
- `start_search` → `mcp__desktop-commander__start_search`
- `get_more_search_results` → `mcp__desktop-commander__get_more_search_results`
- `stop_search` → `mcp__desktop-commander__stop_search`
- 其余工具同理（前缀一致）。

