## Why

The runtime currently enforces strong preparation through Stage 5, but final drafting is still a single write of `final_draft_tex` and `rewrite_report_md`. That leaves too much freedom in the last step, weakens the effect of earlier planning, and provides no gated review loop per target section.

## What Changes

- Add scope-level paragraph segmentation as persisted runtime truth after manuscript analysis
- Add section-level rewrite plans derived from approved condensation planning
- Replace one-shot final drafting with a gated section loop: prepare section, draft, count-check, render review artifact, wait for approval, then continue
- Add a final output-target step and bundle rendering step that copies used images into the chosen output directory

## Capabilities

### New Capabilities

- `segmented-section-gated-drafting`: The runtime supports scope segmentation, section-level rewrite plans, section-by-section gated drafting, and final bundle rendering.

### Modified Capabilities

- `database-ssot-gate-runtime`: Stage 6 no longer ends with a single `persist_final_outputs`; it becomes a multi-action gated drafting loop.

## Impact

- DB schema expands with section-loop drafting tables.
- Gate logic becomes substep-aware inside stage_2, stage_5, and stage_6.
- Final outputs are rendered only after all sections are approved and the output target is confirmed.
