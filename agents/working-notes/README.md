# Working Notes

Use this directory for important working information that should remain reviewable after a task is complete.

These notes are shared across agents. They should help later agents or a human understand what happened, why decisions were made, and what remains uncertain.

## Suggested Files

- `specification.md`: user-facing specification, scope, requirements, non-goals, acceptance criteria, and open questions.
- `task-list.md`: task breakdown, dependencies, ownership, status, and next actions.
- `task-state.md`: durable orchestration state for active multi-agent work.
- `task-log.md`: chronological progress, handoffs, decisions, blockers, and status changes.
- `architectural-decisions.md`: key architectural decision briefs.
- `review-notes.md`: review findings, responses, and unresolved concerns.
- `qa-notes.md`: pre-implementation test plan, test harness notes, validation checklist, commands run, outcomes, feedback loops, and remaining test gaps.

Create task-specific files when a task needs more detail, using clear names such as `2026-05-02-auth-refactor.md`.

## Specification Document

Use this structure for `[GO:plan]` or Plan mode output:

```text
# Specification

## Summary

## Goals

## Non-Goals

## Users or Stakeholders

## Requirements

## Acceptance Criteria

## Constraints

## Architecture Notes

## Data, API, or Integration Notes

## Test and Validation Expectations

## Release, Migration, or Rollback Considerations

## Risks

## Open Questions
```

## Task List

Use this structure for `[GO:plan]` or Plan mode output:

```text
# Task List

## Status Legend

- Not Started
- Blocked
- In Progress
- In Review
- In QA
- Done
- Deferred

## Tasks

| ID | Task | Owner | Status | Dependencies | Files or Areas | Acceptance Criteria | Next Action |
| --- | --- | --- | --- | --- | --- | --- | --- |

## Integration Checkpoints

## Blockers

## Deferred Work
```

## Task State

Use this structure as durable shared state for active multi-agent work:

```text
# Task State

## Current Task

ID:
Status:
Owner:
Decision Owner:
Last Updated:

## Summary

## Dependencies

## Blockers

## Ownership

| Area or File | Owner | Notes |
| --- | --- | --- |

## Decisions

## Test State

Test Plan:
Expected Failing Tests:
Current Result:
Remaining Gaps:

## Review State

Reviewer:
Status:
Findings:
Re-review Required:

## QA State

Tester/QA:
Status:
Feedback:
Retest Required:

## Release Readiness

Docs:
Migrations:
Config or Environment:
Deployment Risk:
Rollback Notes:
User-Facing Acceptance:

## Next Action
```

## Architectural Decision Brief

Use this structure for key architectural decisions:

```text
## Decision: <short title>

Date:
Owner: Architect
Status: Proposed | Accepted | Superseded

Problem or Question:

Context:

Options Considered:

Selected Option:

Reasoning:

Consequences:
```

## General Working Note

Use this structure for other important agent notes:

```text
## Note: <short title>

Date:
Owner:
Type: Handoff | Finding | Blocker | Test Result | Decision | Context
Status: Open | Resolved | Informational

Summary:

Details:

Related files:

Next action:
```

## Test-First QA Note

Use this structure when Tester/QA defines the test approach before implementation:

```text
## Test Plan: <short title>

Date:
Owner: Tester/QA
Status: Draft | Ready for Implementation | Running | Passed | Needs Changes

Acceptance Criteria:

Test Cases:

Harness, Fixtures, or Mocks:

Commands or Manual Checks:

Expected Initial Failures:

Developer Feedback:

Final Results:

Remaining Gaps:
```
