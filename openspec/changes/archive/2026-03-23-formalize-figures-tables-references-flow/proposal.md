## Why

The current skill references figure, table, and citation norms in background guidance, but it still lacks a dedicated execution flow for handling them as first-class manuscript elements. As a result, Stage 1 can finish without a persisted inventory of visuals and references, Stage 4 can approve a condensation plan without explicit figure/table/reference decisions, and Stage 5 can silently drop or weakly placeholder supporting elements during drafting. This makes the workflow unstable for LaTeX manuscripts where figures, tables, citations, and bibliography structure are part of the scientific argument rather than optional decoration.

## What Changes

- Add a dedicated supporting-elements flow that is distributed across Stage 1, Stage 4, and Stage 5 rather than introduced as a standalone stage.
- Add a deterministic helper script to extract figure, table, citation, and bibliography inventories from a single-file `.tex` manuscript.
- Extend `manuscript-profile.json` with persisted supporting-elements inventory fields.
- Extend `target-settings.json` with user-facing figure/table and reference-handling preferences.
- Extend `condensation-plan.md` with explicit figure/table and reference planning sections.
- Update the main skill contract, artifact protocol, stage workflow, and stage playbooks so that supporting elements become part of the formal stage gates.
- Add a dedicated supporting-elements reference playbook.

## Capabilities

### New Capabilities

- `supporting-elements-flow-clarification`: Define how figures, tables, citations, and bibliography structure are inventoried, planned, and migrated across Stage 1, Stage 4, and Stage 5.

### Modified Capabilities

- `stage1-playbook-clarification`: Require a persisted supporting-elements inventory before Stage 1 may complete.
- `stage2-playbook-clarification`: Add confirmed target preferences for figure/table handling and reference handling.
- `stage3-playbook-clarification`: Include caption, table-title, citation-sentence, and reference-presentation guidance in the style profile.
- `stage4-playbook-clarification`: Require explicit figure/table and reference migration decisions in the approved condensation plan.
- `stage5-playbook-clarification`: Require approved supporting-elements decisions to be respected in the final LaTeX draft.

## Impact

- Affects the core contract in `paper-condenser/SKILL.md`.
- Adds one deterministic helper script under `paper-condenser/scripts/`.
- Extends artifact templates and artifact protocol documentation.
- Adds one new reference playbook and updates Stage 1 through Stage 5 playbooks.
