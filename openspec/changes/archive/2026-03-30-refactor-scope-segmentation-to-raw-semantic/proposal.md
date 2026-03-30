## Why

The current runtime lets scripts persist `scope_segments` as if they were the final source units for downstream rewrite planning. That is too strong a responsibility for deterministic segmentation. Scripts can reliably extract raw blocks, but they cannot reliably decide which blocks should be merged into semantic writing units. This weakens Stage 5 and Stage 6 because section plans and section provenance can overfit script boundaries instead of LLM-reviewed argument units.

## What Changes

- Split Stage 2 into three gated actions: manuscript analysis, raw scope segmentation, and semantic source unit consolidation
- Replace `scope_segments` as the downstream write-source truth with a dual-layer model:
  - `raw_scope_segments`
  - `semantic_source_units` plus membership / element mappings
- Require Stage 5 section rewrite planning and Stage 6 section provenance to bind primarily to semantic units
- Add a new rendered view for semantic source units and renumber the downstream rendered views

## Capabilities

### New Capabilities

- `raw-semantic-source-layer`: The runtime distinguishes deterministic raw segmentation from LLM-authored semantic source units.

### Modified Capabilities

- `database-ssot-gate-runtime`: Stage 2 now requires both raw segmentation and semantic consolidation before downstream writing stages can proceed.
- `segmented-section-gated-drafting`: Section rewrite plans and section drafts use semantic source units as their primary provenance path.

## Impact

- Runtime DB schema expands with semantic-unit tables and renames the segmentation truth layer.
- Gate logic becomes stricter in Stage 2.
- Rendered view numbering and template mapping shift from `08/09` to `08/09/10`.
