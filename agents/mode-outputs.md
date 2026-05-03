# Mode Outputs

Use this as the quick reference for what each activation tag should produce.

| Mode | Tag | Purpose | Primary Output | Working Notes | Next Step |
| --- | --- | --- | --- | --- | --- |
| Ideation | `[GO:idea]` | Explore possibilities before choosing a direction. | Idea themes, option set, critiques, promising directions, and open questions. | `ideation.md`, `options.md`, `decision-candidates.md` | Use `[GO:plan]` for the selected direction. |
| Planning | `[GO:plan]` | Turn a direction into a clear buildable specification. | Specification document, task list, dependencies, acceptance criteria, and risks. | `specification.md`, `task-list.md`, `task-state.md`, `architectural-decisions.md` | Use `[GO]` when ready to implement. |
| Implementation | `[GO]` | Build, test, review, and prepare delivery. | Code changes, test results, review status, release readiness, and final synthesis. | `task-state.md`, `qa-notes.md`, `review-notes.md`, `task-log.md`, `architectural-decisions.md` | Deliver or return to `[GO:plan]` if scope changes. |

## Output Progression

```text
[GO:idea] -> candidate directions
[GO:plan] -> specification and task list
[GO] -> implemented and validated change
```

## Choosing a Mode

- Use `[GO:idea]` when you want breadth, alternatives, and better questions.
- Use `[GO:plan]` when you want scope, acceptance criteria, dependencies, and a work plan.
- Use `[GO]` when the target is clear enough to implement with test-first validation.

