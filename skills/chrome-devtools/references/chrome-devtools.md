# Chrome DevTools MCP: notes (condensed)

## Core tool groups

- Page lifecycle: `list_pages`, `new_page`, `select_page`, `navigate_page`, `close_page`
- Page understanding: `take_snapshot`, `evaluate_script`, `take_screenshot`
- Interaction: `click`, `fill`, `fill_form`, `hover`, `press_key`, `type_text`, `drag`, `upload_file`
- Debugging: `list_console_messages`, `get_console_message`, `list_network_requests`, `get_network_request`
- Waiting and dialogs: `wait_for`, `handle_dialog`
- Audits: `lighthouse_audit`, `performance_start_trace`, `performance_stop_trace`, `performance_analyze_insight`

## Best-fit use cases

- Frontend debugging
- Network and console inspection
- Accessibility / SEO / best-practice audit
- Performance tracing

## Key rule

- Take a fresh snapshot before interacting.
