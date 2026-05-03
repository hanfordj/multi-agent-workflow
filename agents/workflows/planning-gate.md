# Planning Gate Workflow

This workflow is active when a user prompt includes `[GO:plan]` or when the session is explicitly running in Plan mode.

## Purpose

Use this workflow to turn an idea or request into a clear specification and task list before implementation begins.

Planning mode is heavier on Orchestrator activity, user clarification, scope control, dependency mapping, and acceptance criteria. It should not implement code unless the user later asks for implementation with `[GO]`.

## Planning Principles

- Prefer clear specification over premature implementation.
- Ask the user for missing product, design, data, integration, or acceptance details when assumptions would be risky.
- Record decisions, open questions, risks, and scope boundaries in durable working notes.
- Produce outputs that a future `[GO]` implementation run can execute without rediscovering the task.

## Workflow

1. Intake
   - Orchestrator summarizes the user's request.
   - Orchestrator identifies the goal, users, constraints, expected behavior, and visible outputs.
   - Orchestrator lists unclear requirements and asks targeted questions.

2. Specification
   - Orchestrator writes or updates `agents/working-notes/specification.md`.
   - If top-level working notes contain prior task content, Orchestrator archives that content or writes the new plan into task-specific notes before updating current files.
   - Architect contributes design constraints, architectural risks, system boundaries, and decision points when needed.
   - Tester/QA contributes acceptance criteria and validation expectations.

3. Task Decomposition
   - Orchestrator writes or updates `agents/working-notes/task-list.md`.
   - For durable history, Orchestrator links or mirrors current top-level files to task-specific notes when the task is likely to span agents, turns, or dependent implementation work.
   - Break work into epics, tasks, dependencies, owners, files or modules, and integration checkpoints.
   - Mark tasks that need Architect, Developer, Reviewer, or Tester/QA involvement.

4. Readiness Review
   - Orchestrator checks that the specification has goals, scope, non-goals, acceptance criteria, dependencies, risks, and open questions.
   - Orchestrator checks that the task list has clear ownership, status, dependencies, and next actions.
   - Orchestrator escalates remaining blockers to the user.

5. Planning Output
   - Orchestrator summarizes the specification and task list.
   - Orchestrator names open questions and implementation risks.
   - Orchestrator tells the user what is ready for `[GO]` implementation and what still needs clarification.

## Required Outputs

Planning mode should write:

- `agents/working-notes/specification.md`
- `agents/working-notes/task-list.md`

For larger projects, also write or update:

- `agents/working-notes/task-state.md`
- `agents/working-notes/architectural-decisions.md`

## User Clarification Triggers

Ask the user before finalizing the plan when:

- Acceptance criteria are missing or subjective.
- The request has multiple plausible interpretations.
- A design, architecture, or data decision changes scope or risk.
- External credentials, APIs, environments, or deployment targets are required.
- Security, privacy, migration, compatibility, or rollback expectations are unclear.
