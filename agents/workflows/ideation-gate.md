# Ideation Gate Workflow

This workflow is active when a user prompt includes `[GO:idea]`.

## Purpose

Use this workflow to explore possibilities before committing to a plan or implementation. Ideation mode should increase the quality of options, questions, and tradeoff awareness.

Ideation should stay divergent long enough to be useful, then converge into a short list of promising candidate directions. It should not produce implementation tasks unless the user asks to move into `[GO:plan]`.

## Ideation Principles

- Separate exploration from commitment.
- Generate multiple distinct options before ranking them.
- Include user/customer perspective, feasibility, constraints, risks, and surprising alternatives.
- Make assumptions visible.
- End with recommended next questions or a clear handoff to `[GO:plan]`.

## Roles

- Orchestrator: frames the ideation prompt, manages rounds, keeps scope visible, and synthesizes output.
- Explorer: generates broad possibilities, variants, adjacent ideas, and unconventional approaches.
- User Advocate: evaluates ideas from the end-user, customer, operator, or stakeholder perspective.
- Architect: comments on technical feasibility, system fit, and major constraints when relevant.
- Critic: pressure-tests ideas for risks, weak assumptions, cost, complexity, and failure modes.
- Synthesizer: groups ideas into themes, identifies promising directions, and recommends next steps.

## Workflow

1. Frame
   - Orchestrator restates the ideation goal.
   - Orchestrator identifies known constraints, audience, success signals, and open questions.
   - If top-level ideation notes contain prior task content, Orchestrator archives that content or writes the new ideation into task-specific notes before updating current files.
   - Orchestrator records assumptions in `agents/working-notes/ideation.md`.

2. Diverge
   - Explorer generates multiple distinct ideas or approaches.
   - User Advocate adds user needs, pain points, adoption concerns, and experience opportunities.
   - Architect adds feasibility notes when the ideas are technical.
   - Orchestrator records options in `agents/working-notes/options.md`.

3. Challenge
   - Critic reviews options for risks, hidden costs, ambiguity, weak assumptions, and failure modes.
   - Orchestrator records critique and unresolved questions.

4. Synthesize
   - Synthesizer groups ideas into themes.
   - Synthesizer identifies candidate directions and decision criteria.
   - Orchestrator records candidates in `agents/working-notes/decision-candidates.md`.

5. Output
   - Orchestrator summarizes strongest themes, promising directions, discarded or lower-confidence ideas, open questions, and recommended next mode.
   - If a direction is ready to specify, recommend `[GO:plan]`.
   - If more exploration is needed, recommend another `[GO:idea]` prompt with sharper framing.

## Required Outputs

Ideation mode should write or update:

- `agents/working-notes/ideation.md`
- `agents/working-notes/options.md`
- `agents/working-notes/decision-candidates.md`

For technical ideas, it may also update:

- `agents/working-notes/architectural-decisions.md`

## Ideation Output Structure

```text
## Ideation Summary

Goal:
Audience:
Constraints:
Assumptions:

## Themes

## Options

## Critique

## Candidate Directions

## Open Questions

## Recommended Next Mode
```
