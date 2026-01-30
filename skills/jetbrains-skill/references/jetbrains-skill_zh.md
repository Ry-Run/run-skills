# jetbrains-skill：摘录与整理

加载建议：
- 需要核对工具名/参数/限制时再加载
- 需要编写调用提示词（例如要求必须传 `projectPath`、超时、截断策略等）时再加载

## 版本与定位

- 从 IntelliJ IDEA *2025.2* 起，IDE 可集成 MCP Server（插件链接在官方文档中提供），允许外部客户端（Claude Desktop、Cursor、VS Code、Windsurf 等）调用 IDE 提供的工具。

## 外部客户端配置（在 IDE 侧完成）

路径：设置 → 工具 → MCP 服务器

- 启用 MCP 服务器
- 客户端自动配置：为指定客户端“自动配置”（会自动更新该客户端 JSON 配置）
- 手动配置：复制 SSE 配置或 Stdio 配置，粘贴到客户端配置中
- 修改后重启客户端生效

### 查看/打开客户端配置文件
IDE UI 提供“打开客户端设置文件”选项用于检查是否已更新；也可“复制配置”粘贴到剪贴板。

## Brave Mode（无需确认执行）

IDE 支持“无需确认即可运行 shell 命令或运行配置（Brave 模式）”：
- 作用：允许外部客户端在不每次弹确认的情况下执行终端命令或运行配置
- 风险：自动化更强，但误操作成本更高

## 支持的工具（按官方文档顺序）

说明：大多数工具都有 `projectPath` 参数。官方建议：如已知，请始终提供 `projectPath`，以减少歧义调用。

### 运行与配置

- `get_run_configurations`
  - 返回当前项目的运行配置列表（可能含命令行/工作目录/环境变量等附加信息）
  - 参数：`projectPath`

- `execute_run_configuration`
  - 运行指定运行配置并等待其在超时内完成
  - 参数：`configurationName`、`timeout`（毫秒）、`maxLinesCount`、`truncateMode`、`projectPath`
  - 返回：退出码、输出、成功状态

### 代码检查与导航

- `get_file_problems`
  - 用 IntelliJ 检查指定文件错误/警告，返回问题列表（严重性、描述、位置）
  - 限制：只能分析项目目录内文件；行号/列号从 1 开始
  - 参数：`filePath`（相对项目根目录）、`errorsOnly`、`timeout`、`projectPath`

- `get_symbol_info`
  - 获取文件某位置的符号信息（类似“快速文档”），可能返回声明片段
  - 参数：`filePath`、`line`（1-based）、`column`（1-based）、`projectPath`

- `rename_refactoring`
  - 语义级重命名（会更新全项目引用），优先于纯文本替换
  - 参数：`pathInProject`、`symbolName`（区分大小写）、`newName`（区分大小写）、`projectPath`

### 项目结构信息

- `get_project_dependencies`
  - 返回项目依赖列表
  - 参数：`projectPath`

- `get_project_modules`
  - 返回项目模块及类型
  - 参数：`projectPath`

- `get_repositories`
  - 返回项目 VCS 根目录列表（多仓库项目）
  - 参数：`projectPath`

### 文件与目录

- `get_all_open_file_paths`
  - 返回当前打开编辑器中的所有文件路径（相对项目根目录）
  - 参数：`projectPath`

- `open_file_in_editor`
  - 在 IDE 编辑器中打开文件
  - 参数：`filePath`（相对项目根目录）、`projectPath`

- `list_directory_tree`
  - 以树形伪图显示目录内容（类似 `tree`），官方建议优先于 `ls/dir`
  - 参数：`directoryPath`、`maxDepth`、`timeout`、`projectPath`

- `find_files_by_name_keyword`
  - 用索引搜索“文件名包含关键字”的文件（区分大小写）
  - 限制：仅匹配名称不匹配路径；不含库/外部依赖；不支持 glob
  - 参数：`nameKeyword`、`fileCountLimit`、`timeout`、`projectPath`

- `find_files_by_glob`
  - 用 glob 匹配“相对路径”查找文件（可指定子目录）
  - 参数：`globPattern`（相对项目根）、`subDirectoryRelativePath`（可选）、`addExcluded`、`fileCountLimit`、`timeout`、`projectPath`

- `get_file_text_by_path`
  - 读取文件文本内容（二进制文件会报错；超大文件按 `truncateMode` 截断并标记“内容已截断”）
  - 参数：`pathInProject`、`truncateMode`、`maxLinesCount`、`projectPath`

- `create_new_file`
  - 在项目内创建新文件（父目录自动创建）
  - 参数：`pathInProject`、`text`（可选）、`overwrite`、`projectPath`

- `replace_text_in_file`
  - 在文件内查找替换文本（修改后自动保存）
  - 返回：`ok` / `project dir not found` / `file not found` / `could not get document` / `no occurrences found`
  - 参数：`pathInProject`、`oldText`、`newText`、`replaceAll`、`caseSensitive`、`projectPath`

- `reformat_file`
  - 重新格式化文件（对指定路径文件应用 IDE 格式化）
  - 参数：`path`（相对项目根目录）、`projectPath`

### 搜索

- `search_in_files_by_text`
  - 用 IDE 搜索引擎在项目内搜索文本子串；匹配用 `||` 高亮
  - 参数：`searchText`、`directoryToSearch`（可选，相对项目根）、`fileMask`（可选，如 `*.java`）、`caseSensitive`、`maxUsageCount`、`timeout`、`projectPath`

- `search_in_files_by_regex`
  - 用 IDE 搜索引擎在项目内按正则搜索；匹配用 `||` 高亮
  - 参数：`regexPattern`、`directoryToSearch`、`fileMask`、`caseSensitive`、`maxUsageCount`、`timeout`、`projectPath`

### 终端

- `execute_terminal_command`
  - 在 IDE 集成终端执行 shell 命令
  - 特性/限制（官方描述）：
    - 执行前检查进程是否仍在运行
    - 输出限制为 2000 行（超出截断）
    - 超时会中断并提示
    - 未开启 Brave Mode 时通常需要用户确认
  - 参数：`command`、`executeInShell`、`reuseExistingTerminalWindow`、`timeout`、`maxLinesCount`、`truncateMode`、`projectPath`

