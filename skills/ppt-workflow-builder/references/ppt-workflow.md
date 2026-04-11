# PPT Workflow Reference

Derived from the workflow described in the Linux.do topic `1782304`.

## Stage 1: deck framing

Use prompts that force these decisions first:

- Who is the audience?
- What action or conclusion should they leave with?
- What is the deck tone: persuasive, analytical, teaching, report, or narrative?
- How many slides should the deck roughly contain?

## Stage 2: JSON outline

Expected outline shape:

```json
{
  "title": "Deck title",
  "audience": "Target audience",
  "goal": "Presentation goal",
  "slides": [
    {
      "id": 1,
      "section": "Opening",
      "title": "Slide title",
      "goal": "What this slide must accomplish",
      "key_points": ["Point 1", "Point 2"],
      "visual_hint": "Chart / timeline / comparison / hero statement"
    }
  ]
}
```

## Stage 3: research pass

For each slide or section, collect:

- supporting facts
- source links
- examples or case studies
- visuals or data candidates
- open questions that still need answers

Do not move into final visuals while factual holes remain.

## Stage 4: slide planning draft

Translate each slide into:

- message
- evidence
- visual structure
- presenter intent

Example prompt skeleton:

```text
Expand this slide outline into a presentation planning draft.
For each slide, write:
1. core message
2. supporting evidence
3. recommended visual structure
4. speaker note intent
Keep every slide focused on one job.
```

## Stage 5: SVG slide generation

Prefer one SVG per slide with a consistent 16:9 canvas.

Default expectations:

- consistent visual system across slides
- readable hierarchy
- presentation-grade typography and spacing
- visuals driven by the slide goal, not generic templates

Example prompt skeleton:

```text
Generate a single-slide SVG for slide {n}.
Use a 16:9 presentation canvas.
The slide goal is: ...
The key points are: ...
The visual structure should be: ...
Do not create a text wall.
```

## Stage 6: assembly

If SVG import is acceptable, use the generated SVG pages as the visual source of truth and assemble the final deck from them. If the delivery requires editable native slides, rebuild or refine inside the deck tool after the SVG stage.

