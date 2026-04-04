# Playwright MCP: notes (condensed)

## Core tool groups

- Browser/session: `browser_navigate`, `browser_tabs`, `browser_close`, `browser_resize`
- Page understanding: `browser_snapshot`, `browser_take_screenshot`, `browser_evaluate`
- Interaction: `browser_click`, `browser_type`, `browser_fill_form`, `browser_select_option`, `browser_press_key`, `browser_hover`, `browser_drag`, `browser_file_upload`
- Diagnostics: `browser_console_messages`, `browser_network_requests`
- Waiting and dialogs: `browser_wait_for`, `browser_handle_dialog`
- Escape hatch: `browser_run_code`

## Best-fit use cases

- Scripted user flows
- E2E reproduction
- Form-heavy interactions

## Key rule

- Snapshot before actions; use snapshot refs, not screenshots, for targeting.
