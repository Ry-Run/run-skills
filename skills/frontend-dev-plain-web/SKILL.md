---
name: frontend-dev-plain-web
description: Use when building a webpage with plain HTML, CSS, and JavaScript from requirements or references, especially when you want a lightweight workflow for research, implementation, browser verification, and focused debugging without framework-heavy processes.
---

# Frontend Development (Plain CSS, HTML, JS)

## Quick start

Goal: ship a plain-web page with the minimum necessary workflow instead of stitching together ad hoc research, coding, and browser checks.

## Best fit

- Landing pages, static pages, and simple interactive pages.
- Tasks that should stay in plain HTML, CSS, and JavaScript.
- Code-first work starting from requirements, references, or rough ideas.
- Cases where full browser verification matters before calling the work done.

## Recommended workflow

1. Shape the page goal and constraints first.
2. Research in this order:
   - `context7` for official docs, APIs, and standard usage.
   - `ref-skill` for GitHub examples, issues, and real-world code.
   - `grok-search` for concepts, tradeoffs, best practices, hard-to-find technical questions, and all non-technical research. State the Grok model when it is known.
3. If available, use `frontend-design` to improve layout and visual direction.
4. If available, use `uncodixfy` while generating UI so the page does not fall into generic AI patterns.
5. Implement locally with `desktop-commander`.
6. Verify the page with `playwright-skill`.
7. If behavior is still unclear, debug with `chrome-devtools`.
8. Use `adapt` only when responsive work is actually needed.
9. Use `polish` only for a final refinement pass.

## Verification checklist

- The page loads correctly.
- Core interactions work.
- Layout is sane for the required viewport targets.
- Obvious console or network problems are checked when needed.

## Guardrails

- Keep the default path light; do not start with task managers, Figma, GitHub, Vercel, or other unrelated skills.
- Prefer `playwright-skill` for mainline verification and `chrome-devtools` for targeted debugging.
- Do not escalate to a framework unless the user explicitly wants one.
- Use optional design skills only when they materially improve the page.
