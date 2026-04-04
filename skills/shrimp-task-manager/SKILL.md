---
name: shrimp-task-manager
description: "Use Shrimp Task Manager MCP for structured task analysis, decomposition, execution guidance, tracking, and verification. Use it when the main need is to manage a task system with dependencies and completion checks, rather than just expose a reasoning chain."
---

# Shrimp Task Manager

## Quick start

Goal: turn a large task into an explicit task system with analysis, decomposition, execution guidance, and verification.

Reference notes: `skills/shrimp-task-manager/references/shrimp-task-manager.md`

## Best-fit use cases

- Multi-step implementation with dependencies.
- Research-heavy engineering work.
- Tasks needing explicit acceptance criteria and progress tracking.
- Cases where you want a scored verification step before claiming done.

## Recommended workflow

1. Analyze the task: `analyze_task` or `plan_task`
2. Break it down: `split_tasks`
3. Inspect and execute one task at a time: `list_tasks`, `get_task_detail`, `execute_task`
4. Update tasks as reality changes: `update_task`
5. Verify completion: `verify_task`

## Important behavior

- `execute_task` gives guidance; it does not perform the work for you.
- `verify_task` should reflect the real outcome against the recorded criteria.
- Use `research_mode` when a technical investigation spans multiple passes.

## Guardrails

- Do not fabricate requirements; gather evidence first.
- Keep task granularity reasonable and dependencies explicit.
- Avoid deleting unfinished tasks unless there is a clear reason.

## References

- Condensed notes: `skills/shrimp-task-manager/references/shrimp-task-manager.md`
