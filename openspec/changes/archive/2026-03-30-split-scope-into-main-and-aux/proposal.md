## Why

The current Stage 2 model treats scope as a single range. That is too rigid for chapter-to-journal rewriting. In practice, users often want to rewrite one chapter or one section from a larger report or thesis, while still needing background, literature review, or method overview from elsewhere in the source document. If the scope is hard-bounded to only the target chapter, later stages lose legitimate supporting material and the logic chain becomes harder to preserve.

## What Changes

- Replace the single `scope + scope_locator` analysis model with a `main_scope + main_scope_locator + aux_scopes[*]` model
- Keep raw segmentation in one table, but tag every raw segment with `scope_role`, `scope_bucket_id`, and `scope_label`
- Allow semantic source units to mix main and aux raw members while preserving role tracking through member rows
- Update Stage 5 and Stage 6 provenance rendering so users can see whether a section relies on main material, aux support, or both

## Capabilities

### New Capabilities

- `main-aux-scope-model`: Stage 2 supports one main rewrite target plus zero-to-many auxiliary support ranges.

### Modified Capabilities

- `raw-semantic-source-layer`: Raw segmentation now captures main/aux role metadata and semantic units may mix both layers.
- `segmented-section-gated-drafting`: Section plans and section reviews must expose the main/aux composition of semantic provenance.

## Impact

- Stage 2 payload schema changes directly.
- Raw scope segment rows gain additional role fields.
- Stage 5/6 rendered provenance becomes more explicit.
