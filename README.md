# Multi-Agent Workflow

This repository contains a lightweight framework for coordinating multiple coding agents around software work. It is designed for Codex-style terminal sessions where you want the default behavior to stay simple, but you can opt into a structured multi-agent process when the task benefits from planning, architecture, test-first implementation, review, and QA.

## Quick Start

Use normal prompts for ordinary single-agent work:

```text
Update the README with setup instructions.
```

Use `[GO:plan]` when you want a planning pass before implementation:

```text
[GO:plan] Build a user profile settings page with email preferences, avatar upload, and account deletion.
```

Use `[GO]` when you want the multi-agent implementation workflow:

```text
[GO] Implement the planned user profile settings page.
```

The activation rules live in `AGENTS.md`.

## Activation Modes

### Default Mode

If a prompt does not include `[GO]` or `[GO:plan]`, the assistant should work as a normal single coding agent. The multi-agent workflow should not activate automatically.

Use this for small edits, quick questions, focused fixes, or anything that does not need orchestration.

### Planning Mode: `[GO:plan]`

Use `[GO:plan]` when the task is still fuzzy, large, risky, or likely to require user clarification.

Planning mode is heavier on Orchestrator-led specification work. It should produce:

- `agents/working-notes/specification.md`
- `agents/working-notes/task-list.md`

For larger projects, it may also update:

- `agents/working-notes/task-state.md`
- `agents/working-notes/architectural-decisions.md`

Planning mode should clarify requirements, define scope and non-goals, identify risks, create acceptance criteria, break work into tasks, map dependencies, and identify which agents should be involved later.

It should not implement code unless the user later asks for implementation with `[GO]`.

### Implementation Mode: `[GO]`

Use `[GO]` when you want the full multi-agent coding workflow.

The implementation flow is:

1. Intake
2. Planning
3. Architecture
4. Test Design
5. Implementation
6. Test/QA Feedback
7. Review
8. Release Readiness
9. Final Synthesis

The detailed workflow is in `agents/workflows/multi-agent-coding.md`.

## Agent Roles

### Orchestrator

Coordinates the work from intake to final delivery. The Orchestrator breaks work into tasks, assigns ownership, tracks state, manages handoffs, escalates unclear decisions to the user, and synthesizes the final result.

Persona file: `agents/personas/orchestrator.md`

### Architect

Designs the approach, identifies impacted systems, records key architectural decisions, and gives implementation guidance. For important decisions, the Architect writes a brief covering the problem, options considered, selected option, and reasoning.

Persona file: `agents/personas/architect.md`

### Tester/QA

Drives the test-first workflow. Tester/QA defines test cases, harnesses, fixtures, expected failures, and validation checks before production implementation begins where possible. After implementation, Tester/QA runs tests and sends feedback back to the Developer when changes are needed.

Persona file: `agents/personas/tester-qa.md`

### Developer

Implements the requested changes using the Architect's guidance and Tester/QA's test plan. The Developer respects assigned ownership, keeps changes focused, and responds to QA or review feedback.

Persona file: `agents/personas/developer.md`

### Reviewer

Reviews the final post-QA diff for defects, regressions, missed requirements, security concerns, maintainability issues, and release-readiness gaps. If code changes after review, the workflow sends the work back through QA and review before final delivery.

Persona file: `agents/personas/reviewer.md`

## Test-Driven Flow

The framework expects a TDD-style implementation loop:

1. Tester/QA turns acceptance criteria into tests, expected failures, or a validation harness.
2. Developer implements production code against that test target.
3. Tester/QA runs the planned tests and reports failures, coverage gaps, or testability concerns.
4. Developer addresses the feedback.
5. Reviewer reviews the final post-QA diff.
6. Any code change after review returns to Tester/QA and Reviewer before final delivery.

If test-first work is not practical for a task, the exception should be documented in the working notes.

## Durable Working Notes

The multi-agent workflow uses `agents/working-notes/` to keep important context available across agents and later review.

Common files:

- `specification.md`: planning output, requirements, scope, acceptance criteria, risks, and open questions.
- `task-list.md`: task breakdown, dependencies, owners, statuses, files or areas, and next actions.
- `task-state.md`: current durable orchestration state for active multi-agent work.
- `task-log.md`: chronological progress, handoffs, blockers, and status changes.
- `architectural-decisions.md`: key architectural decision briefs.
- `review-notes.md`: review findings, responses, and unresolved concerns.
- `qa-notes.md`: test plans, harness notes, commands, results, QA feedback, and remaining gaps.

Templates and guidance live in `agents/working-notes/README.md`.

## Model Policy

All agents inherit the model selected in the UI by default.

Per-role model overrides are optional and should only be used when there is a clear reason, such as cost control, latency, complex architecture, or high-risk review. Model policy lives in `agents/model-policy.md`.

## Editing the Framework

Edit activation rules:

- `AGENTS.md`

Edit workflows:

- `agents/workflows/planning-gate.md`
- `agents/workflows/multi-agent-coding.md`

Edit personas:

- `agents/personas/orchestrator.md`
- `agents/personas/architect.md`
- `agents/personas/developer.md`
- `agents/personas/reviewer.md`
- `agents/personas/tester-qa.md`

Edit shared note templates:

- `agents/working-notes/README.md`

Edit model selection policy:

- `agents/model-policy.md`

## Recommended Usage Pattern

For a small task, skip the tags and work normally.

For a medium or large feature, start with `[GO:plan]`. Review the generated specification and task list, answer open questions, then use `[GO]` when the plan is ready for implementation.

For risky changes, migrations, cross-module refactors, security-sensitive work, or anything with unclear acceptance criteria, prefer `[GO:plan]` first. The extra planning pass gives the agents a shared target and leaves a written record a human can inspect later.
