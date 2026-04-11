---
name: ppt-workflow-builder
description: Use when creating a PPT or slide deck from a topic, article, research corpus, or rough brief, especially when you need a repeatable workflow for audience framing, JSON outline generation, slide research, planning drafts, and SVG-first slide production before assembling the final deck.
---

# PPT Workflow Builder

## Quick start

Goal: build slide decks through a repeatable workflow instead of jumping straight into page-by-page slide writing.

Reference notes:
- `skills/ppt-workflow-builder/references/ppt-workflow.md`
- `skills/ppt-workflow-builder/references/ppt-workflow_zh.md`

## Best fit

- Conference decks, client presentations, internal reports, pitch decks, teaching slides, and proposal decks.
- Cases where the source material is messy and needs to be turned into a clear slide narrative.
- Tasks that benefit from separate stages for structure, research, planning, and final slide visuals.
- Cases where an SVG-first workflow is acceptable before final PPT assembly.

## Core workflow

1. Frame the deck before writing slides:
   - Identify audience, presentation goal, tone, and expected deck length.
   - Define the single through-line the deck should prove.
2. Build a structured outline first:
   - Create a JSON outline that lists sections, slide goals, and key claims.
   - Do not start page visuals before the outline is stable.
3. Research slide content by section:
   - Use `context7` for official technical docs when the deck is about libraries, APIs, or standards.
   - Use `ref-skill` for GitHub examples, issues, implementation references, and real-world code.
   - Use `grok-search` for broader research, comparisons, framing, best practices, supporting examples, and non-technical material. State the Grok model when it is known.
4. Turn the outline into a planning draft:
   - For each slide, define the core message, supporting evidence, visual type, and speaker intent.
   - Kill slides that do not move the argument forward.
5. Generate final slide pages in an SVG-first format:
   - Produce each slide as a separate SVG page with a consistent 16:9 canvas.
   - Keep the layout presentation-grade, editable, and suitable for later PPT import.
6. Assemble the PPT:
   - Import the SVG pages into presentation software when that workflow is acceptable.
   - If native PPT editing is required later, use the SVG pages as the visual source of truth while rebuilding or refining slides inside the deck tool.

## Working files

Use a predictable artifact chain:

- `deck-outline.json` for the approved slide structure.
- `deck-research.md` for gathered facts, references, and supporting notes.
- `deck-plan.md` for per-slide messages, layouts, and evidence.
- `slides/slide-01.svg`, `slides/slide-02.svg`, ... for final page assets.

Do not skip directly from topic to final slides. The outline and planning files are part of the deliverable workflow.

## Prompt pattern

Use a staged prompt pattern rather than one-shot prompting:

1. Ask for or infer audience, goal, tone, and length.
2. Generate JSON outline.
3. Research missing facts and supporting material.
4. Produce slide planning draft.
5. Generate final SVG pages.

The reference files include reusable prompt scaffolds for each stage.

## Guardrails

- Do not start with slide decoration before the deck argument is clear.
- Do not generate final slide pages before the outline is approved.
- Do not let every slide become a text wall; every page needs a single job.
- Do not treat research notes as slide copy. Rewrite for presentation flow.
- Do not use a single one-shot mega prompt when a staged workflow is more reliable.
- If a factual gap blocks a slide, go back to research instead of improvising.

