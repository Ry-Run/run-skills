---
name: playwright-skill
description: "Use Playwright MCP for deterministic browser automation: navigate pages, fill forms, reproduce user flows, and run lightweight end-to-end interactions. Use it when scripted cross-browser execution matters more than DevTools-level debugging."
---

# Playwright Skill

## Quick start

Goal: reproduce a user flow in a controlled browser session and inspect what happened.

Reference notes: `skills/playwright-skill/references/playwright-skill.md`

## Best-fit use cases

- Form filling, login, uploads, and multi-step flows.
- Reproducing UI bugs step by step.
- Browser-based checks where deterministic actions matter.
- Lightweight E2E validation and screenshots.

## Recommended workflow

1. Navigate to the page.
2. Capture a snapshot before interacting.
3. Use references from the snapshot for clicks, typing, fills, and selections.
4. Wait explicitly for text, disappearance, or time when state changes.
5. Inspect console or network if the flow fails.

## Prefer Playwright when

- The main task is executing user actions.
- You need deterministic reproduction rather than DevTools analysis.
- You want concise network/console inspection around a scripted flow.

## Guardrails

- Snapshot before actions; do not rely on screenshots for element targeting.
- Use `browser_run_code` sparingly, only when normal tools are insufficient.
- Treat file uploads and destructive clicks as high-risk if user data may change.

## References

- Condensed notes: `skills/playwright-skill/references/playwright-skill.md`
