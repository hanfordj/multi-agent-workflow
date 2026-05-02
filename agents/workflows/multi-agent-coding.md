# Multi-Agent Coding Workflow

This workflow is active only when a user prompt includes `[GO]`.

For planning-only work, use `[GO:plan]` or Plan mode and follow `agents/workflows/planning-gate.md`.

## Core Principle

Use multiple agents when coordination improves quality, but keep the process lightweight. Small tasks may use only the Orchestrator plus the roles that materially help.

Follow a test-driven development flow when implementation is required: define and, where possible, create or run failing tests, test cases, or a harness before the Developer writes production code, then use test feedback to guide implementation changes.

All agents inherit the UI-selected model by default. Use `agents/model-policy.md` for any explicit per-role model guidance.

Maintain durable shared state in `agents/working-notes/` for project-scale work. Conversation context is not a substitute for task state when work spans multiple agents, turns, or dependent tasks.

## Roles

- Orchestrator: owns task intake, routing, state, and final synthesis.
- Architect: owns design direction and implementation strategy.
- Developer: owns code changes and responds to test feedback.
- Reviewer: owns code review and risk assessment.
- Tester/QA: owns pre-implementation test design, validation, feedback, and quality status.

## Workflow

1. Intake
   - Orchestrator summarizes the request.
   - Orchestrator extracts acceptance criteria.
   - Orchestrator identifies constraints, unknowns, and likely files or systems.

2. Planning
   - Orchestrator decomposes project-scale work into epics, tasks, dependencies, and integration checkpoints.
   - Orchestrator assigns preliminary owners and file or module ownership before parallel work begins.
   - Orchestrator records durable state in `agents/working-notes/task-state.md` or a task-specific working note.
   - Orchestrator escalates unclear requirements, conflicting acceptance criteria, risky tradeoffs, or blocked decisions to the user.

3. Architecture
   - Architect inspects relevant context.
   - Architect proposes the implementation approach.
   - Architect records key architectural decisions in `agents/working-notes/` using the architectural decision brief structure.
   - Orchestrator records key decisions and prepares test-first development scope.

4. Test Design
   - Tester/QA converts acceptance criteria into test cases before production implementation begins.
   - Tester/QA identifies or builds the test harness, fixtures, mocks, and manual validation checks needed for the task.
   - Tester/QA creates and, where possible, runs expected failing tests before production code changes.
   - Tester/QA records the test plan, test files, commands, expected initial failures, and any TDD exception reason in `agents/working-notes/`.
   - Orchestrator confirms the Developer has enough test guidance to implement against.

5. Implementation
   - Developer edits files within the assigned scope.
   - Developer uses the Tester/QA test plan and expected failures to drive implementation.
   - Developer respects Orchestrator-assigned file, module, or task ownership.
   - Developer follows existing project conventions.
   - Developer records notable choices, changed files, and any blockers.

6. Test/QA Feedback
   - Tester/QA runs the planned tests, harness, and relevant regression checks.
   - Tester/QA evaluates whether implementation is thoroughly testable, not merely passing.
   - Tester/QA reports pass/fail status, coverage gaps, unclear behavior, and testability concerns.
   - Developer addresses failed tests or testability feedback, then returns changes to Tester/QA.
   - Orchestrator repeats the Developer and Tester/QA loop until unresolved issues are accepted, fixed, or explicitly deferred.

7. Review
   - Reviewer inspects the final post-QA diff and relevant surrounding code.
   - Reviewer reports blocking findings first.
   - Developer addresses accepted findings.
   - Any code change after review returns to Test/QA Feedback and then back to Review before final delivery.

8. Release Readiness
   - Orchestrator confirms documentation, migrations, configuration, environment variables, deployment risk, rollback notes, and user-facing acceptance criteria where relevant.
   - Tester/QA confirms validation status and remaining gaps.
   - Reviewer confirms no unresolved blocking findings remain.

9. Final Synthesis
   - Orchestrator summarizes changes.
   - Orchestrator includes validation performed.
   - Orchestrator names residual risks or follow-ups.

## Handoff Template

Use this shape for agent handoffs:

```text
Role:
Task:
Relevant context:
Files or areas:
Ownership:
Dependencies:
Constraints:
Expected output:
```

## Shared State

Track shared state in `agents/working-notes/` by default for project-scale work:

- Task id
- Status
- Owner
- Dependencies
- Blockers
- Request summary
- Acceptance criteria
- Decisions
- Assigned work
- File or module ownership
- Test plan
- Changed files
- Review status
- Review findings
- QA status
- Test results
- Testability feedback
- Release readiness
- Next action
- Open risks

## Working Notes

Use `agents/working-notes/` for important working information that should remain reviewable after the task is complete. These notes are for later agents and humans who need to understand how the work progressed.

Recommended files:

- `specification.md`: user-facing specification, scope, requirements, non-goals, acceptance criteria, and open questions.
- `task-list.md`: task breakdown, dependencies, ownership, status, and next actions.
- `task-state.md`: durable orchestration state for active multi-agent work.
- `task-log.md`: chronological progress, handoffs, decisions, blockers, and status changes.
- `architectural-decisions.md`: key architectural decision briefs.
- `review-notes.md`: review findings, responses, and unresolved concerns.
- `qa-notes.md`: pre-implementation test plan, test harness notes, validation checklist, commands run, outcomes, feedback loops, and remaining test gaps.

Architectural decision briefs should use this structure:

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

## Completion Criteria

A task is ready for final delivery when:

- The requested behavior has been implemented or the blocker is clearly explained.
- Failing tests, test cases, or a validation harness were created or specified before production implementation, or the reason for skipping TDD is documented.
- Any code changes made after QA or review were returned through Tester/QA and Reviewer before final delivery.
- Review has found no unresolved blocking issues.
- Relevant validation has passed, or unrun validation and remaining testability gaps are explicitly reported.
- Documentation, migrations, configuration, environment variables, deployment risk, rollback notes, and user-facing acceptance have been addressed where relevant.
- The final answer is concise and actionable.
