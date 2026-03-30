## ADDED Requirements

### Requirement: SQLite is the only runtime source of truth

The package MUST persist runtime state in a single SQLite database under the artifact root.

#### Scenario: A runtime workspace is initialized

- **WHEN** runtime bootstrap succeeds
- **THEN** `.paper-condenser-tmp/<document-slug>/paper-condenser.db` exists
- **AND** the DB is treated as the only runtime source of truth
- **AND** Markdown views and final outputs are rendered from DB state rather than treated as editable truth

### Requirement: Runtime progression is gate-driven

The package MUST use a single gate entry to determine the only allowed next action.

#### Scenario: A runtime workspace is resumed

- **WHEN** `gate_runtime.py` is run against an existing `artifact-root`
- **THEN** it returns `workflow_stage`
- **AND** it returns `next_action`
- **AND** it returns blockers and pending confirmations when progression is not allowed

### Requirement: Runtime views are render-only

The package MUST render human-readable Markdown views from the DB and MUST NOT treat them as runtime truth.

#### Scenario: A stage write succeeds

- **WHEN** `stage_runtime.py` persists stage data
- **THEN** the runtime view files are re-rendered from the database
- **AND** the Agent is expected to treat them as read-only

### Requirement: Final outputs are rendered from DB state

The package MUST keep final draft and rewrite report as output files, but they MUST be rendered from DB-backed content.

#### Scenario: Final drafting completes

- **WHEN** `persist_final_outputs` succeeds
- **THEN** `.paper-condenser-tmp/<document-slug>/final-draft.tex` exists
- **AND** `.paper-condenser-tmp/<document-slug>/rewrite-report.md` exists
- **AND** neither file is treated as runtime truth
