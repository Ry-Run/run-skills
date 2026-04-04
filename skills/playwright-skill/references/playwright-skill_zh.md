# Playwright MCP：摘录说明

## 核心工具分组

- 浏览器 / 会话：`browser_navigate`、`browser_tabs`、`browser_close`、`browser_resize`
- 页面理解：`browser_snapshot`、`browser_take_screenshot`、`browser_evaluate`
- 交互：`browser_click`、`browser_type`、`browser_fill_form`、`browser_select_option`、`browser_press_key`、`browser_hover`、`browser_drag`、`browser_file_upload`
- 诊断：`browser_console_messages`、`browser_network_requests`
- 等待与弹窗：`browser_wait_for`、`browser_handle_dialog`
- 兜底入口：`browser_run_code`

## 最适合的问题

- 脚本化用户流程
- E2E 复现
- 表单交互密集场景

## 关键规则

- 交互前先抓快照；元素定位要用快照引用，不要靠截图。
