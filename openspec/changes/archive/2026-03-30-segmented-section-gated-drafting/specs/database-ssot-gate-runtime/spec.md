## MODIFIED Requirements

### Requirement: Runtime progression is gate-driven

The package MUST use a single gate entry to determine the only allowed next action.

#### Scenario: The runtime enters final drafting

- **WHEN** Stage 5 planning is complete
- **THEN** gate may return `prepare_section_drafting`, `persist_section_draft`, `approve_section_draft`, `persist_output_target`, or `render_final_output_bundle`
- **AND** it MUST NOT allow a one-shot final drafting bypass

### Requirement: Runtime views are render-only

The package MUST render human-readable Markdown views from the DB and MUST NOT treat them as runtime truth.

#### Scenario: Section drafting state changes

- **WHEN** section drafting, approval, or output-target persistence succeeds
- **THEN** the drafting-board and section-review views are re-rendered from the database
- **AND** the Agent is expected to treat them as read-only
