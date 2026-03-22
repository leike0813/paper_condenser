## Context

The package already has a Stage 4 artifact and a high-level Stage 4 stage definition, but it still does not provide an authoritative recipe for how condensation planning is performed, persisted, and approved. The next risk is inconsistent planning behavior, where one agent jumps from broad ideas directly into writing, another never records a complete outline and length allocation, and a third treats verbal user agreement as approval without writing it into `condensation-plan.md`.

## Goals / Non-Goals

**Goals:**
- Turn Stage 4 into a concrete condensation-planning playbook
- Define the minimum completion standard for the six existing sections in `condensation-plan.md`
- Make Stage 5 depend on an explicit approved plan
- Keep the current Markdown template shape and script interfaces unchanged

**Non-Goals:**
- Add new scripts
- Add new status fields or approval metadata
- Convert `condensation-plan.md` into JSON or another structured format
- Redesign Stage 5 in this change

## Decisions

- Keep `condensation-plan.md` exactly as-is structurally.
- Represent Stage 4 completeness through the content completeness of the five planning sections plus the existing approval line.
- Continue using `## Approval` with `Status: not approved|approved` as the only explicit approval marker.
- Require the planning order to move from core message to priorities to outline to length allocation to omit/merge strategy, then to approval.
- Add a dedicated `references/stage4-playbook.md` so the main contract stays compact while still being precise.
- Keep Stage 4 free of Stage 5 drafting behavior.

## Risks / Trade-offs

Keeping the existing Markdown-only structure avoids schema churn and keeps the skill readable, but it also means Stage 4 completion is judged from content adequacy plus a single approval line rather than a richer state model. That trade-off is acceptable because this change is about tightening planning behavior, not introducing a workflow engine.
