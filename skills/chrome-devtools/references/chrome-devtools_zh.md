# Chrome DevTools MCP：摘录说明

## 核心工具分组

- 页面生命周期：`list_pages`、`new_page`、`select_page`、`navigate_page`、`close_page`
- 页面理解：`take_snapshot`、`evaluate_script`、`take_screenshot`
- 交互：`click`、`fill`、`fill_form`、`hover`、`press_key`、`type_text`、`drag`、`upload_file`
- 调试：`list_console_messages`、`get_console_message`、`list_network_requests`、`get_network_request`
- 等待与弹窗：`wait_for`、`handle_dialog`
- 审计：`lighthouse_audit`、`performance_start_trace`、`performance_stop_trace`、`performance_analyze_insight`

## 最适合的问题

- 前端调试
- 网络与控制台检查
- 可访问性 / SEO / 最佳实践审计
- 性能追踪

## 关键规则

- 交互前先取最新快照。
