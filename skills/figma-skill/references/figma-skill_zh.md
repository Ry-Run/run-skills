# Figma MCP：摘录说明

## 核心工具分组

- 读取设计上下文：`get_design_context`、`get_metadata`、`get_screenshot`、`get_variable_defs`
- 搜索 / 复用设计系统：`search_design_system`
- 直接写入 Figma：`use_figma`
- 把网页抓进 Figma：`generate_figma_design`
- 创建文件 / 图表：`create_new_file`、`generate_diagram`
- Code Connect：`get_code_connect_map`、`get_code_connect_suggestions`、`send_code_connect_mappings`、`add_code_connect_map`

## 关键规则

- design-to-code 优先 `get_design_context`。
- 创建组件前先搜设计系统资产。
- 已存在或已抓取过的文件，后续更新优先用 `use_figma`。
- `generate_figma_design` 只用于首次抓取网页 / 页面。
