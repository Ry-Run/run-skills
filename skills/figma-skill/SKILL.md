---
name: figma-skill
description: "Use Figma MCP for design-to-code, code-to-Figma, design system search, Code Connect, and direct canvas edits. Use it when a task needs real Figma file context or writes to a Figma document, rather than generic browser automation."
---

# Figma Skill

## Quick start

Goal: work against real Figma files instead of guessing from screenshots or loose descriptions.

Reference notes: `skills/figma-skill/references/figma-skill.md`

## Default tool choices

- Design understanding: `get_design_context`
- File structure only: `get_metadata`
- Screenshots: `get_screenshot`
- Design-system lookup: `search_design_system`
- Direct canvas writes: `use_figma`
- First-time webpage capture: `generate_figma_design`

## Recommended workflow

1. Extract `fileKey` and `nodeId` from the Figma URL.
2. Use `get_design_context` by default for design-to-code work.
3. Before creating components, search the design system for reusable assets.
4. Use `use_figma` for edits inside an existing file.
5. Use `generate_figma_design` only when capturing a web page/view into Figma for the first time.

## Code Connect workflows

- Read mappings: `get_code_connect_map`
- Get suggestions: `get_code_connect_suggestions`
- Save approved mappings: `send_code_connect_mappings`
- Add a direct mapping: `add_code_connect_map`

## Guardrails

- Prefer `get_design_context` over `get_metadata` when actual implementation guidance is needed.
- Search the design system before recreating components.
- Treat broad destructive canvas edits as high-risk; confirm before mass deletion/rewrite.

## References

- Condensed notes: `skills/figma-skill/references/figma-skill.md`
