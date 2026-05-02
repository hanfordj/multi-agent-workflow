# Multi-Agent Coding Workflow

This directory contains an editable baseline for coordinating multiple coding agents.

Future prompts in this terminal should activate this workflow only when the prompt includes `[GO]`, as defined in the repository root `AGENTS.md`.

Planning-only prompts should use `[GO:plan]` or run in Plan mode. Planning output should produce a specification document and task list before implementation begins.

## Roles

- Orchestrator: coordinates the workflow, delegates work, tracks state, and synthesizes the final answer.
- Architect: shapes design, interfaces, tradeoffs, and implementation strategy.
- Developer: implements the agreed changes.
- Reviewer: reviews code for defects, regressions, security, maintainability, and missed requirements.
- Tester/QA: defines and runs validation, checks acceptance criteria, and reports quality status.

## Where To Edit

Personas live in `agents/personas/`.

The workflow lives in `agents/workflows/multi-agent-coding.md`.

The planning gate lives in `agents/workflows/planning-gate.md`.

Shared working notes and templates live in `agents/working-notes/`.

Model policy lives in `agents/model-policy.md`. By default, all agents inherit the UI-selected model.
