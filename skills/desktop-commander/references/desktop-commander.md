# Desktop Commander Skill: notes (condensed)

Use this reference when you need to confirm tool names, categories, or the key security limitations.

## Tool categories

Note: depending on the host client, tools may appear as short names (e.g. `read_file`) or namespaced (e.g. `mcp__desktop-commander__read_file`). This skill primarily uses the namespaced form.

### Configuration
- `get_config`: get full server config (JSON): `blockedCommands`, `defaultShell`, `allowedDirectories`, `fileReadLineLimit`, `fileWriteLineLimit`, `telemetryEnabled`, etc.
- `set_config_value`: set one config key.

### Terminal
- `start_process`: start a program/command; detect when ready for input.
- `interact_with_process`: send input to a running process and get responses.
- `read_process_output`: read output from a running process (paging supported).
- `force_terminate`: force-terminate a terminal session.
- `list_sessions`: list active terminal sessions.
- `list_processes`: list running OS processes.
- `kill_process`: terminate a process by PID.

### Filesystem
- `read_file`: read local files, URLs, Excel, and PDFs with pagination (supports negative offsets to read from the end).
- `read_multiple_files`: read multiple files in one call.
- `write_file`: write text/Excel with `rewrite` or `append` modes. For PDFs use `write_pdf`.
- `write_pdf`: create or modify PDFs (insert/delete pages) from markdown (supports HTML/CSS and SVG).
- `create_directory`: create a directory (or ensure it exists).
- `list_directory`: recursive listing with `depth` parameter.
- `move_file`: move or rename files/directories.
- `start_search`: streaming search by file name or content (can search Excel content).
- `get_more_search_results`: paginate search results (offset/length).
- `stop_search`: stop an active search.
- `list_searches`: list active searches.
- `get_file_info`: metadata for files/directories (Excel includes sheet info).

### Text editing
- `edit_block`: targeted text replacement for text files; range-based updates for Excel.

### Analytics
- `get_usage_stats`: usage statistics.
- `get_recent_tool_calls`: recent tool call history (args + outputs).
- `give_feedback_to_desktop_commander`: open feedback form.

## security limitations (important)

- `allowedDirectories` only restricts filesystem tool operations, not terminal commands. Terminal commands can still access files outside `allowedDirectories`.
- recommends making config changes in a separate chat, to avoid accidentally expanding access while solving unrelated tasks.
- `fileWriteLineLimit` exists to encourage small, chunked writes (default 50 lines) to reduce token waste and avoid losing work when messages truncate.

