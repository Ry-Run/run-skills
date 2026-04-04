---
name: chrome-devtools
description: "Use Chrome DevTools MCP for real-browser debugging: console and network inspection, runtime state checks, Lighthouse audits, and performance tracing. Use it when diagnosis and browser internals matter more than scripted cross-browser automation."
---

# Chrome DevTools

## Quick start

Goal: inspect and debug a real page with DevTools-style tooling: snapshots, console, network, screenshots, audits, and traces.

Reference notes: `skills/chrome-devtools/references/chrome-devtools.md`

## Best-fit use cases

- Frontend debugging in a real browser.
- Checking console errors, network requests, or runtime state.
- Running Lighthouse or performance traces.
- Interacting with pages where DOM state matters.

## Recommended workflow

1. Open or select the target page.
2. Take an accessibility snapshot before interacting.
3. Click/fill/type only after identifying the right element UID.
4. Inspect console/network when behavior is unclear.
5. Use Lighthouse or trace tools for quality/performance work.

## Prefer Chrome DevTools when

- You need console, network, trace, or audit tooling.
- You want direct DOM evaluation on the loaded page.
- The task is debugging a web app, not just reproducing a user flow.

## Guardrails

- Always use the latest snapshot before clicking or typing.
- For PDFs, prefer `screenshot` on specific pages.
- Use performance tracing selectively; it is heavier than normal inspection.

## References

- Condensed notes: `skills/chrome-devtools/references/chrome-devtools.md`
