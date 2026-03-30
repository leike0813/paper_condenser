## Purpose

Define Stage 5 and the final drafting output path after the DB-backed runtime refactor.

## Requirements

### Requirement: Stage 5 is DB-backed and gated

Stage 5 MUST persist final drafting results to SQLite and MUST render final outputs from DB state.

#### Scenario: Final drafting is completed

- **WHEN** final bundle rendering succeeds
- **THEN** the DB stores the final draft and rewrite report content
- **AND** the runtime renders `final-draft.tex` and `rewrite-report.md`
- **AND** the workflow may only reach `stage_7_completed` after both rendered files exist
