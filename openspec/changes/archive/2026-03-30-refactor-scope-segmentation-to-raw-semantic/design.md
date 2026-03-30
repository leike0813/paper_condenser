# Design

## Decision

Adopt a dual-layer source model:

- `raw_scope_segments`
  - deterministic, script-produced, low-semantic facts
- `semantic_source_units`
  - LLM-reviewed, writeable source units for Stage 5 and Stage 6

## Stage 2 flow

Stage numbering stays unchanged. `stage_2_manuscript_analysis` now has three formal actions:

1. `persist_manuscript_analysis`
2. `persist_raw_scope_segments`
3. `persist_semantic_source_units`

The gate must not allow Stage 3 until all three are complete.

## Source binding policy

- Stage 5 section rewrite plans may bind:
  - `semantic_unit:<unit_id>`
  - supporting-element / citation / bibliography refs
- Stage 6 section draft provenance may bind only:
  - `semantic_unit:<unit_id>`

Raw segments are never the formal write-source path once semantic units exist.

## Rendered views

- Keep `07-scope-segments.md` for raw blocks only
- Add `08-semantic-source-units.md`
- Shift downstream rendered views:
  - `09-section-rewrite-plan.md`
  - `10-section-drafting-board.md`

## Compatibility

The old action `persist_scope_segments` is retained only as a deprecated shim that fails and points callers to `persist_raw_scope_segments`.
