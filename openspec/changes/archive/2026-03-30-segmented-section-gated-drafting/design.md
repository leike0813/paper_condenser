# Design

## Runtime strategy

Keep the current stage numbering, but add finer `next_action` branches:

- `stage_2_manuscript_analysis`
  - `persist_manuscript_analysis`
  - `persist_scope_segments`
- `stage_5_condensation_plan`
  - `persist_condensation_plan`
  - `persist_section_rewrite_plan`
- `stage_6_final_drafting`
  - `prepare_section_drafting`
  - `persist_section_draft`
  - `approve_section_draft`
  - `persist_output_target`
  - `render_final_output_bundle`

## Scope segmentation

- Segment only within the approved manuscript-analysis scope.
- Persist deterministic segments at least at paragraph granularity.
- Preserve figure, table, and display blocks as standalone segments.
- Require a machine-readable `scope_locator` inside manuscript analysis so scripts can segment deterministically.

## Section drafting loop

- Section granularity is top-level target-outline sections.
- Each section has:
  - a rewrite plan row
  - source mappings
  - a mutable draft row
  - provenance rows
  - event log rows
- Count validation uses the planned section count with a default tolerance of `±15%`.
- Each section must be approved before the next section is activated.

## Final bundle

- After all section approvals, persist the output target.
- Render final outputs only after the output target is confirmed.
- Copy only the actually referenced image assets into `<output_dir>/images/`.
- Rewrite `\includegraphics{...}` paths to the copied image paths.
