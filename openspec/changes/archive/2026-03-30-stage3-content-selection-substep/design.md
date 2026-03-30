# Design

## Decision

Keep Stage 3 as `stage_3_target_settings`, but split it into four gated actions:

1. `persist_target_settings_basics`
2. `persist_content_selection_board`
3. `confirm_content_selection`
4. `finalize_target_settings`

## Content-selection model

The content-selection board is backed by:

- `content_selection_items`
- `content_selection_item_units`

Each item is a semantic aggregation for user review, not a mechanical raw-segment mapping. Every item must still point to one or more semantic source units, and the rendered board must expose the underlying raw-member provenance through those units.

## Stage 3 flow

- Basic target settings are persisted first.
- The agent then writes a content-selection board with suggested `must_keep`, `simplify_first`, and `must_avoid` items.
- The user reviews and adjusts those items.
- The confirmed result is summarized back into `target_settings`.
- Only then may `user_confirmed=true`.

## Downstream consumption

- Stage 5 section rewrite plans must consume the Stage 3 triad.
- `simplify_first` is not equivalent to `must_avoid`; it means compress or rewrite aggressively while still preserving the content in some reduced form.

## Rendered views

- Add `11-content-selection-board.md`
- Keep `03-target-settings.md` as the compact summary view
