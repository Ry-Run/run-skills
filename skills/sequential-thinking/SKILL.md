---
name: sequential-thinking
description: "Use Sequential Thinking MCP for explicit reasoning steps with revisions, branching, and uncertainty handling. Use it when the main need is to structure analysis, planning, or decision-making, rather than manage a persistent task system."
---

# Sequential Thinking

## Quick start

Goal: externalize a long reasoning chain when the problem is ambiguous, multi-stage, or likely to need course correction.

Primary entry point:
- `mcp__sequential_thinking__sequentialthinking`

Reference notes: `skills/sequential-thinking/references/sequential-thinking.md`

## When to use it

- Complex debugging with multiple hypotheses.
- Planning or design with tradeoffs.
- Problems where you may need to revise earlier assumptions.
- Multi-step analysis where the answer is not obvious upfront.

## When not to use it

- Simple factual lookups.
- Straightforward code edits with already-clear scope.
- Cases where direct execution is faster than explicit deliberation.

## Workflow

1. Start with an estimated `totalThoughts`.
2. Record each step with increasing `thoughtNumber`.
3. Mark revisions or branches when you change course.
4. Stop only when the solution is actually stable.

## Guardrails

- Keep thoughts decision-oriented, not verbose for its own sake.
- Revise earlier thoughts when evidence changes.
- Do not use it as a substitute for gathering facts from code or tools.

## References

- Condensed notes: `skills/sequential-thinking/references/sequential-thinking.md`
