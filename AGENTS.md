# Agent Operating Instructions

## Multi-Agent Activation Gate

Use the implementation workflow in this repository only when the user's prompt includes the exact tag `[GO]`.

Use the ideation workflow when the user's prompt includes the exact tag `[GO:idea]`.

Use the planning workflow when the user's prompt includes the exact tag `[GO:plan]` or when the current session is explicitly running in Plan mode.

If the user's prompt includes more than one exact activation tag among `[GO]`, `[GO:idea]`, and `[GO:plan]`:

- Do not activate any workflow yet.
- Have the Orchestrator ask the user which single mode to use.
- Name the detected tags and briefly explain the mode choice needed.
- Continue only after the user clarifies the intended mode.

If none of `[GO]`, `[GO:idea]`, or `[GO:plan]` is present, and the session is not running in Plan mode:

- Do not invoke or simulate the multi-agent workflow.
- Work as a single coding agent using the user's request directly.
- You may mention that structured modes are available with `[GO:idea]`, `[GO:plan]`, or `[GO]` if it would help, but do not activate them automatically.

If `[GO:idea]` is present:

- Use `agents/workflows/ideation-gate.md`.
- Focus on divergent exploration, user/customer perspective, feasibility, critique, synthesis, and promising next directions.
- Do not converge into an implementation plan too early.
- Write ideation output into the ideation working notes in `agents/working-notes/`.
- End with clear candidate directions and recommended next questions or next mode.

If `[GO:plan]` is present, or the session is running in Plan mode:

- Use `agents/workflows/planning-gate.md`.
- Focus on Orchestrator-led clarification, specification, task decomposition, dependencies, risks, and acceptance criteria.
- Ask the user for missing specification details before implementation planning becomes guesswork.
- Write the planning output into a clear specification document and task list using the structures in `agents/working-notes/`.
- Do not implement code unless the user later asks for implementation with `[GO]`.

If `[GO]` is present:

- Use the coordination model in `agents/workflows/multi-agent-coding.md`.
- Apply the role personas in `agents/personas/`.
- Apply the model policy in `agents/model-policy.md`; by default, all agents inherit the UI-selected model.
- Keep the Orchestrator responsible for task routing, context handoff, progress tracking, and final synthesis.
- Use the Architect for design decisions before implementation when the task affects structure, contracts, or architecture.
- Use the Developer for implementation.
- Use the Reviewer for code review, risk analysis, and maintainability checks.
- Use the Tester/QA role for validation strategy, test execution, and quality sign-off.

## Editable Agent Files

Edit baseline personas here:

- `agents/personas/orchestrator.md`
- `agents/personas/architect.md`
- `agents/personas/developer.md`
- `agents/personas/reviewer.md`
- `agents/personas/tester-qa.md`
- `agents/personas/explorer.md`
- `agents/personas/critic.md`
- `agents/personas/synthesizer.md`
- `agents/personas/user-advocate.md`

Edit the coordination process here:

- `agents/workflows/ideation-gate.md`
- `agents/workflows/multi-agent-coding.md`
- `agents/workflows/planning-gate.md`

Understand mode outputs here:

- `agents/mode-outputs.md`

Edit model selection policy here:

- `agents/model-policy.md`
