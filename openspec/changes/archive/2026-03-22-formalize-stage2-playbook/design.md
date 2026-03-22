## Context

The package already has a Stage 2 artifact and a high-level Stage 2 stage definition, but it still does not provide an authoritative recipe for how target settings are collected, persisted, read back, and confirmed. The next risk is inconsistent target-setting behavior, where one agent confirms too early, another keeps draft answers only in chat, and a third pulls Stage 3 or Stage 4 questions forward before the target-setting bundle is locked.

## Goals / Non-Goals

**Goals:**
- Turn Stage 2 into a concrete target-setting playbook
- Define how `target-settings.json` behaves before and after explicit confirmation
- Make Stage 3 depend on a fully confirmed Stage 2 artifact
- Keep the current JSON shape and script interfaces unchanged

**Non-Goals:**
- Add new scripts
- Expand `target-settings.json` with new status or question fields
- Redesign Stage 3 through Stage 5 in this change
- Reopen the file-path-only decision made for Stage 1

## Decisions

- Keep `target-settings.json` exactly as-is.
- Represent draft progress through partial field population plus `user_confirmed=false`.
- Require the collection order to move from core target settings to keep/avoid constraints, then to full readback.
- Treat `user_confirmed=true` as the only formal Stage 2 completion marker.
- Add a dedicated `references/stage2-playbook.md` so the main contract stays compact while still being precise.
- Keep Stage 2 free of style-analysis and condensation-plan questions.

## Risks / Trade-offs

Keeping the current schema avoids churn and preserves continuity with existing artifacts, but it means unresolved Stage 2 issues are represented only through still-empty fields and `user_confirmed=false`. That trade-off is acceptable because this change is about tightening execution behavior, not expanding the data model.
