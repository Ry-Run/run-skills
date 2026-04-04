# Figma MCP: notes (condensed)

## Core tool families

- Read design context: `get_design_context`, `get_metadata`, `get_screenshot`, `get_variable_defs`
- Search/reuse design system: `search_design_system`
- Write to Figma: `use_figma`
- Capture web page into Figma: `generate_figma_design`
- Create files / diagrams: `create_new_file`, `generate_diagram`
- Code Connect: `get_code_connect_map`, `get_code_connect_suggestions`, `send_code_connect_mappings`, `add_code_connect_map`

## Key rules

- Prefer `get_design_context` for design-to-code.
- Before creating components, search design system assets.
- Use `use_figma` for updates to an already captured or existing file.
- Use `generate_figma_design` only for first capture of a webpage/view.
