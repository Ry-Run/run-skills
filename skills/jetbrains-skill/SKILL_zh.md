---
name: jetbrains-skill
description: 使用 JetBrains IDE（IntelliJ IDEA 2025.2+）内置的 MCP Server，让外部客户端（Claude Desktop、Cursor、VS Code 等）通过 IDE 提供的工具与项目交互：运行 Run Configuration、在 IDE 终端执行命令、读取/创建/修改项目文件、用 IDE 的索引搜索文本/正则、获取文件检查问题、查询符号信息、执行 rename 重构、列出模块/依赖、打开文件并格式化等。适用于：希望“让 IDE 代替命令行/脚本做代码理解与重构”的场景（尤其是跨语言工程、需要索引/重构/检查能力时）。
---

# JetBrains Skill

## 快速上手

目标：把 JetBrains IDE 的“索引、检查、重构、运行配置、集成终端”能力暴露给外部客户端使用，并保持可控、可审计、可回滚。

摘录与工具列表见：`skills/jetbrains-skill-zh/references/jetbrains-skill.md`。

## 连接与模式

### 外部客户端配置（IDE 内完成）

在 IDE：设置 → 工具 → MCP 服务器：
1) 启用 MCP 服务器
2) 对目标客户端执行“自动配置”（会更新客户端 JSON 配置）；或复制 SSE / Stdio 配置手动粘贴
3) 重启客户端生效

### Brave Mode（无需确认执行）

IDE 支持开启 “无需确认即可运行 shell 命令或运行配置（Brave 模式）”。
这会显著提高自动化效率，但安全风险也显著上升（等同于把“点击确认”移除）。
涉及开启/关闭 Brave Mode 时，必须先说明影响范围并获得用户明确确认。

## 工作流决策树

1) 我想用 IDE 的“索引/检查/重构”能力吗？（优先选 IDE 工具，而不是终端）
- 查问题：`get_file_problems`
- 查符号语义/声明：`get_symbol_info`
- 结构化重命名：`rename_refactoring`（优先于纯文本替换）
- 全项目搜索：`search_in_files_by_text` / `search_in_files_by_regex`
- 查文件：已知文件名片段 → `find_files_by_name_keyword`；按路径 glob → `find_files_by_glob`

2) 我只是要读/写项目文件吗？
- 读文件：`get_file_text_by_path`
- 创建新文件：`create_new_file`
- 精确替换文本：`replace_text_in_file`（文件会自动保存）
- 打开文件到 IDE：`open_file_in_editor`
- 格式化：`reformat_file`

3) 我想在 IDE 里“跑东西”吗？
- 列出 run configuration：`get_run_configurations`
- 运行 run configuration 并等待结束：`execute_run_configuration`
- 在 IDE 集成终端执行命令：`execute_terminal_command`（默认可能需要确认；输出有行数上限）

## 强制约束（避免踩坑）

- `projectPath`：如已知，始终传入，减少“选错项目”的歧义。
- 路径范围：部分工具只允许操作“项目目录内文件”，并使用“相对项目根目录”的路径参数（详见参考资料）。
- 行/列从 1 开始：`get_file_problems` / `get_symbol_info` 等位置参数均为 1-based。
- 截断：多工具支持 `maxLinesCount` + `truncateMode`，用于控制返回量；不要依赖默认值处理大输出。
- 安全：执行终端命令/运行配置属于高风险能力；在未开启 Brave Mode 时可能会触发用户确认。任何可能导致数据丢失的命令，必须先明确确认。

## 推荐用法（高价值模式）

### 代码问题定位（IDE 检查优先）
1) `get_file_problems` 找错误/警告 → 2) 结合 `get_symbol_info` 理解符号 → 3) 需要重命名用 `rename_refactoring` → 4) 最后再用 `replace_text_in_file` 做纯文本修补（如果确实合适）。

### 全项目搜索（IDE 搜索优先）
优先 `search_in_files_by_text` / `search_in_files_by_regex`，因为基于 IDE 索引，通常比命令行搜索更快；匹配会用 `||` 高亮。

### 运行与回收输出
运行配置用 `execute_run_configuration`，并把 `timeout` 设置为合理值（毫秒）。终端命令用 `execute_terminal_command`，注意其输出截断/行数限制，必要时把命令改成“输出到文件再读取”。

## 参考资料
- 摘录与工具列表：`skills/jetbrains-skill-zh/references/jetbrains-skill.md`
