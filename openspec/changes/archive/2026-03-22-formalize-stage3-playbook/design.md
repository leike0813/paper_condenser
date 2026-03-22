## Context

The package already has a Stage 3 artifact and a high-level Stage 3 stage definition, but it still does not provide an authoritative recipe for how style analysis is performed, persisted, and judged complete. The next risk is inconsistent style handling, where one agent only describes the manuscript's current style, another jumps directly into rewrite advice, and a third leaves unresolved style preferences only in chat before moving into Stage 4.

## Goals / Non-Goals

**Goals:**
- Turn Stage 3 into a concrete style-analysis playbook
- Define the minimum completion standard for the four existing sections in `style-profile.md`
- Make Stage 4 depend on a usable and explicit style profile
- Keep the current Markdown template shape and script interfaces unchanged

**Non-Goals:**
- Add new scripts
- Add machine-readable status fields or sections to `style-profile.md`
- Convert `style-profile.md` into JSON or another structured format
- Redesign Stage 4 through Stage 5 in this change

## Decisions

- Keep `style-profile.md` exactly as-is structurally.
- Represent Stage 3 completeness through the content completeness of the four existing sections, not through a new status field.
- Require the analysis order to move from source-style observation to problem diagnosis to target guidance to open-question capture.
- Allow unresolved but non-blocking style questions, but require them to be written into `Open Questions`.
- Add a dedicated `references/stage3-playbook.md` so the main contract stays compact while still being precise.
- Keep Stage 3 free of Stage 4 planning questions.

## Risks / Trade-offs

Keeping the existing Markdown-only structure avoids schema churn and keeps the skill readable, but it also means Stage 3 completion is judged from content adequacy rather than a machine-readable status bit. That trade-off is acceptable because this change is about tightening authoring behavior, not introducing a workflow state machine.
