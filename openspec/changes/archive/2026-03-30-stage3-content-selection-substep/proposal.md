## Why

The current Stage 3 runtime only has a single `persist_target_settings` action. In practice that causes agents to throw all Stage 3 questions at the user in one batch, especially the must-keep / must-avoid decisions. Those decisions are the most important part of Stage 3 and need their own gated substep based on previously persisted semantic source units.

## What Changes

- Split Stage 3 into four gated actions:
  - `persist_target_settings_basics`
  - `persist_content_selection_board`
  - `confirm_content_selection`
  - `finalize_target_settings`
- Add a dedicated content-selection board backed by its own tables and rendered view
- Add `simplify_first` as a first-class list alongside `must_keep` and `must_avoid`
- Require Stage 5 section rewrite planning to consume the confirmed Stage 3 triad

## Capabilities

### New Capabilities

- `stage3-content-selection-substep`: Stage 3 now includes a dedicated content-selection review substep built from semantic source units.

### Modified Capabilities

- `database-ssot-gate-runtime`: Stage 3 is now multi-step and gate-driven internally.
- `segmented-section-gated-drafting`: Section rewrite plans now consume `simplify_first` in addition to keep/avoid constraints.

## Impact

- Runtime DB schema expands with content-selection tables.
- Stage 3 gate logic becomes stricter.
- One new rendered view is added: `11-content-selection-board.md`.
