## MODIFIED Requirements

### Requirement: Stage 1 runs through DB-backed intake and inventory

Stage 1 MUST persist deterministic intake and supporting-elements inventory to SQLite before semantic manuscript analysis is considered complete.

#### Scenario: A new manuscript enters the runtime

- **WHEN** Stage 1 begins
- **THEN** the allowed action is `persist_intake_and_inventory`
- **AND** the runtime stores intake metadata and supporting-elements inventory in the database
- **AND** only then may the workflow advance to manuscript analysis persistence
