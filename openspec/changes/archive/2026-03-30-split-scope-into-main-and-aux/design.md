# Design

## Decision

Adopt a dual-scope analysis model:

- `main_scope`
  - the primary rewrite target
- `aux_scopes`
  - zero-to-many support-only ranges used for background, review, method overview, and similar context

The runtime must not treat aux as a second main target.

## Raw layer

`raw_scope_segments` remains a single table, but each row carries:

- `scope_role`
- `scope_bucket_id`
- `scope_label`

Segmentation still stays deterministic and script-driven. The script only extracts facts within approved main/aux ranges.

## Semantic layer

`semantic_source_units` may combine raw members from main and aux. The unit itself does not get a single role. Instead, role information is preserved on member rows and shown in rendered views.

## Downstream provenance

- Stage 5 section rewrite plans still bind primarily to `semantic_unit:<unit_id>`
- Stage 6 section draft provenance still binds only to semantic units
- If a section uses a semantic unit with aux members, the section plan must record why aux support is needed

## Rendering

The following rendered views must surface main/aux provenance:

- `02-manuscript-profile.md`
- `07-scope-segments.md`
- `08-semantic-source-units.md`
- `09-section-rewrite-plan.md`
- `section-reviews/<section_order>-<section_id>.md`
