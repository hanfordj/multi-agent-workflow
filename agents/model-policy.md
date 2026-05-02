# Model Policy

## Default

All agents inherit the model selected in the UI.

Do not assign a different model to a role unless this file explicitly defines an override and the current tool or runtime supports per-agent model selection.

## Policy Format

Use one section per role. Keep `model` set to `inherit` unless you intentionally want a role-specific override.

```yaml
roles:
  orchestrator:
    model: inherit
    reasoning_effort: inherit
    notes: Uses the UI-selected model by default.

  architect:
    model: inherit
    reasoning_effort: inherit
    notes: Uses the UI-selected model by default.

  developer:
    model: inherit
    reasoning_effort: inherit
    notes: Uses the UI-selected model by default.

  reviewer:
    model: inherit
    reasoning_effort: inherit
    notes: Uses the UI-selected model by default.

  tester_qa:
    model: inherit
    reasoning_effort: inherit
    notes: Uses the UI-selected model by default.
```

## Optional Override Guidance

Only use overrides when there is a clear reason, such as cost control, latency, exceptionally complex architecture, or high-risk review.

When adding an override, record:

- Role
- Model
- Reasoning effort, if supported
- Reason for the override
- Expected tradeoff
- Date and owner of the change

Example:

```yaml
roles:
  architect:
    model: gpt-5.5
    reasoning_effort: high
    reason: Complex cross-system architecture decision.
    tradeoff: Higher cost and latency for stronger design reasoning.
    owner: Orchestrator
    date: 2026-05-02
```

## Current Role Policy

```yaml
roles:
  orchestrator:
    model: inherit
    reasoning_effort: inherit

  architect:
    model: inherit
    reasoning_effort: inherit

  developer:
    model: inherit
    reasoning_effort: inherit

  reviewer:
    model: inherit
    reasoning_effort: inherit

  tester_qa:
    model: inherit
    reasoning_effort: inherit
```

