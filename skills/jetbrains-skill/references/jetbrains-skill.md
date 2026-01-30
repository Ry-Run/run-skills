# JetBrains MCP Skill: notes (condensed)

Use this reference to confirm tool names, parameters, and constraints.

## Scope & availability

- Starting with IntelliJ IDEA *2025.2*, the IDE can expose an MCP Server so external clients can use IDE-provided tools.

## Client setup (inside the IDE)

Settings → Tools → MCP Server:
- Enable MCP Server
- Auto-configure supported clients (updates their JSON config), or copy SSE / Stdio config for manual setup
- Restart the external client to apply changes

## Brave Mode (no confirmations)

The IDE can allow connected clients to run shell commands / run configurations without per-action confirmation (“Brave mode”).
This increases automation power and risk. Treat enabling/disabling it as a high-risk change.

## Supported tools (as documented)

Tip: Most tools accept `projectPath`. When known, always pass it to reduce ambiguity.

### Run configurations
- `get_run_configurations`
  - Params: `projectPath`
- `execute_run_configuration`
  - Params: `configurationName`, `timeout` (ms), `maxLinesCount`, `truncateMode`, `projectPath`
  - Returns: exit code, output, success status

### Diagnostics, symbols, refactoring
- `get_file_problems`
  - Checks a file for errors/warnings (IDE inspections)
  - Constraints: project files only; line/column are 1-based
  - Params: `filePath` (relative to project root), `errorsOnly`, `timeout`, `projectPath`
- `get_symbol_info`
  - Symbol info at a file position (similar to “Quick Documentation”)
  - Params: `filePath`, `line` (1-based), `column` (1-based), `projectPath`
- `rename_refactoring`
  - Context-aware rename across the project (prefer over plain text replace)
  - Params: `pathInProject`, `symbolName` (case-sensitive), `newName` (case-sensitive), `projectPath`

### Project structure
- `get_project_dependencies` (params: `projectPath`)
- `get_project_modules` (params: `projectPath`)
- `get_repositories` (params: `projectPath`)

### Files and directories
- `get_all_open_file_paths` (params: `projectPath`)
- `open_file_in_editor` (params: `filePath` (relative), `projectPath`)
- `list_directory_tree` (params: `directoryPath` (relative), `maxDepth`, `timeout`, `projectPath`)
- `find_files_by_name_keyword`
  - Indexed name-only search (case-sensitive); does not match paths; no glob support; project files only
  - Params: `nameKeyword`, `fileCountLimit`, `timeout`, `projectPath`
- `find_files_by_glob`
  - Path glob search (glob is relative to project root)
  - Params: `globPattern`, `subDirectoryRelativePath` (optional), `addExcluded`, `fileCountLimit`, `timeout`, `projectPath`
- `get_file_text_by_path`
  - Reads a text file; binary returns an error; large output can be truncated (marked as truncated)
  - Params: `pathInProject`, `truncateMode`, `maxLinesCount`, `projectPath`
- `create_new_file`
  - Creates a new file (parent dirs auto-created)
  - Params: `pathInProject`, `text` (optional), `overwrite`, `projectPath`
- `replace_text_in_file`
  - Returns：`ok` / `project dir not found` / `file not found` / `could not get document` / `no occurrences found`
  - Targeted find/replace in a file; auto-saves after modification
  - Params: `pathInProject`, `oldText`, `newText`, `replaceAll`, `caseSensitive`, `projectPath`

- `reformat_file`
  - Reformat file via IDE formatter
  - Params: `path` (relative), `projectPath`

### Search
- `search_in_files_by_text`
  - Indexed substring search; matches are highlighted with `||...||`
  - Params: `searchText`, `directoryToSearch` (optional), `fileMask` (optional, e.g. `*.java`), `caseSensitive`, `maxUsageCount`, `timeout`, `projectPath`
- `search_in_files_by_regex`
  - Indexed regex search; matches are highlighted with `||...||`
  - Params: `regexPattern`, `directoryToSearch`, `fileMask`, `caseSensitive`, `maxUsageCount`, `timeout`, `projectPath`

### Terminal
- `execute_terminal_command`
  - Runs a shell command in the IDE integrated terminal
  - Constraints (as documented): checks running state before collecting output; output capped (2000 lines); timeouts are reported; requires confirmation unless Brave Mode is enabled
  - Params: `command`, `executeInShell`, `reuseExistingTerminalWindow`, `timeout`, `maxLinesCount`, `truncateMode`, `projectPath`
