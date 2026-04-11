---
name: frontend-dev-plain-web
description: Use when building a webpage with plain HTML and CSS, and only add JavaScript when the requirements clearly need interaction. It fits lightweight code-first work that needs doc lookup, real-image sourcing, browser verification, and required DevTools checks without framework-heavy processes.
---

# Frontend Development (Plain CSS, HTML, JS)

## Quick start

Goal: ship a plain-web page with the minimum necessary workflow instead of stitching together ad hoc research, coding, image sourcing, fallback handling, and browser checks.

## Best fit

- Landing pages, static pages, and simple interactive pages.
- Tasks that should stay in plain HTML and CSS unless JavaScript is explicitly required.
- Code-first work starting from requirements, references, or rough ideas.
- Cases where full browser verification matters before calling the work done.

## Recommended workflow

1. Shape the page goal and constraints first.
2. Decide whether JavaScript is truly needed. If the requirements do not clearly need interaction or state changes, do not add JavaScript.
3. Research in this order:
   - `context7` for official docs, APIs, and standard usage.
   - `ref-skill` for GitHub examples, issues, and real-world code.
   - `grok-search` for concepts, tradeoffs, best practices, hard-to-find technical questions, and all non-technical research. State the Grok model when it is known.
4. If the page needs imagery, describe the needed scenes in text, generate search keywords, use `grok-search` to find candidate image URLs from sources such as Unsplash, Pexels, Pixabay, or Google Custom Search JSON API, then download the chosen images locally with `desktop-commander`.
5. Validate every chosen image before using it:
   - If a candidate URL returns `404`, `403`, times out, redirects badly, or otherwise fails, pick another image and retry.
   - If a downloaded file is corrupt, unreadable, or does not render correctly, replace it with another candidate.
   - Final HTML and CSS must reference only local image paths, never the remote candidate URLs.
6. If the page requires image-led sections such as a hero, showcase, or primary cards, do not replace them with solid-color blocks, gradient panels, or placeholders when image sourcing fails. Keep retrying with another real image instead.
7. If available, use `frontend-design` to improve layout and visual direction.
8. If available, use `uncodixfy` while generating UI so the page does not fall into generic AI patterns.
9. Implement locally with `desktop-commander`. Keep the layout structured so the footer naturally stays at the bottom even when content is short.
10. Verify the page with `playwright-skill`.
11. Run required checks with `chrome-devtools` for console, network, layout, image loading, and footer placement.
12. Use `adapt` only when responsive work is actually needed.
13. Use `polish` only for a final refinement pass.

## Image handling loop

Treat image selection as a retry loop, not a one-shot step:

1. Describe the visual scene.
2. Generate targeted search keywords.
3. Search for candidates.
4. Download one candidate locally.
5. Check that the local file is actually usable.
6. If any check fails, discard it and repeat with another candidate.
7. Stop only when the page references a working local file and the browser renders it correctly.

## Image-first prompt block

Use this as a reusable rule block when the page should lean on real imagery:

```text
You are a high-end frontend designer and UI/UX expert.

Build a complete responsive webpage with plain HTML and CSS first. Add JavaScript only if the requirements clearly need interaction.

Strict rules:
1. Use real high-resolution photos as primary visual elements. Do not replace image areas with solid color blocks, gradient-only panels, or placeholder images.
2. Hero sections should prefer a large real background image with a readable dark overlay when the design calls for it.
3. Cards and showcase sections should use real photos through <img> or background-image when imagery is part of the design.
4. When images are needed but not provided, first describe the scene, generate search keywords, search image sources, and download the selected files locally. Final HTML and CSS must reference local image paths, not temporary remote placeholders or remote CDN image URLs.
5. If an image URL fails, returns 404, downloads as broken data, or cannot be rendered in the browser, replace it with another candidate image. Do not fall back to a solid-color or gradient block.
6. Do not generate any JavaScript unless the requirements explicitly need interaction.
7. Keep the page modern, responsive, and visually intentional.
8. Make the footer stay at the bottom of the page. When content is short, the footer must still be pushed to the bottom with no large empty area underneath.
```

## Verification checklist

- The page loads correctly.
- Core interactions work.
- Layout is sane for the required viewport targets.
- JavaScript is absent unless the requirements clearly justify it, including no unnecessary `<script>` tags, inline handlers, or extra JS files.
- Images are real assets, are referenced from local paths, and are not left as remote candidate URLs when imagery is required.
- Image requests and rendering are actually valid: no `404`, `403`, broken-image icons, unreadable files, or decode failures.
- Image-led sections are not silently replaced with solid-color or gradient blocks.
- The footer stays at the bottom of the page, including short-content cases.
- `chrome-devtools` checks confirm there are no obvious console, network, image-loading, or layout issues.

## Guardrails

- Keep the default path light; do not start with task managers, Figma, GitHub, Vercel, or other unrelated skills.
- Do not add JavaScript by habit. If HTML and CSS solve the requirement, stop there.
- Do not treat a found image URL as complete. It must become a working local file before use.
- Do not fake image-driven design with solid blocks, gradient placeholders, fake URLs, or failed downloads.
- If one image candidate fails, switch candidates and continue instead of degrading the layout.
- `chrome-devtools` is a required inspection step, not an optional extra.
- Do not escalate to a framework unless the user explicitly wants one.
- Use optional design skills only when they materially improve the page.
