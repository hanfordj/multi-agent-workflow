# Multi-Agent Coding Workflow

This directory contains an editable baseline for coordinating multiple coding agents.

Future prompts in this terminal should activate this workflow only when the prompt includes `[GO]`, as defined in the repository root `AGENTS.md`.

Planning-only prompts should use `[GO:plan]` or run in Plan mode. Planning output should produce a specification document and task list before implementation begins.

Ideation prompts should use `[GO:idea]`. Ideation output should explore options, critique them, synthesize themes, and recommend promising directions before planning begins.

## Roles

- Orchestrator: coordinates the workflow, delegates work, tracks state, and synthesizes the final answer.
- Architect: shapes design, interfaces, tradeoffs, and implementation strategy.
- Developer: implements the agreed changes.
- Reviewer: reviews code for defects, regressions, security, maintainability, and missed requirements.
- Tester/QA: defines and runs validation, checks acceptance criteria, and reports quality status.
- Explorer: generates broad possibilities, alternatives, and adjacent ideas during ideation.
- Critic: pressure-tests ideas for weaknesses, constraints, risks, and bad assumptions.
- Synthesizer: groups ideas into themes and recommends candidate directions.
- User Advocate: evaluates ideas from the end-user, customer, or stakeholder perspective.

## Where To Edit

Personas live in `agents/personas/`.

The workflow lives in `agents/workflows/multi-agent-coding.md`.

The ideation gate lives in `agents/workflows/ideation-gate.md`.

The planning gate lives in `agents/workflows/planning-gate.md`.

Mode outputs are summarized in `agents/mode-outputs.md`.

Shared working notes and templates live in `agents/working-notes/`.

Model policy lives in `agents/model-policy.md`. By default, all agents inherit the UI-selected model.
