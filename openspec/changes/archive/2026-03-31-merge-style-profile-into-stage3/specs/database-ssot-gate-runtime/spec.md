## MODIFIED Requirements

### Requirement: Runtime progression is gate-driven

The package MUST use a single gate entry to determine the only allowed next action.

#### Scenario: A runtime workspace is resumed

- **WHEN** `gate_runtime.py` is run against an existing `artifact-root`
- **THEN** it returns `workflow_stage`
- **AND** it returns `next_action`
- **AND** it returns blockers and pending confirmations when progression is not allowed

#### Scenario: Style profiling remains inside Stage 3

- **WHEN** Stage 3 basics and content selection are complete
- **AND** `style_profile.status` is not yet `complete`
- **THEN** gate remains at `stage_3_target_settings`
- **AND** gate returns `persist_style_profile`
- **AND** it MUST NOT advance to `stage_4_condensation_plan`

#### Scenario: The runtime enters final drafting

- **WHEN** Stage 4 planning is complete
- **THEN** gate may return `prepare_section_drafting`, `persist_section_draft`, `approve_section_draft`, `persist_output_target`, or `render_final_output_bundle`
- **AND** it MUST NOT allow a one-shot final drafting bypass
