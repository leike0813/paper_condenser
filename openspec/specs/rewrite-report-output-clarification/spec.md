## Purpose

Define rewrite report behavior as a DB-backed final output.

## Requirements

### Requirement: Rewrite report is rendered from database-backed final state

The rewrite report MUST be persisted as DB-backed final output content and rendered to file as part of the final drafting stage.

#### Scenario: A completed runtime is inspected

- **WHEN** the runtime reaches `stage_7_completed`
- **THEN** `rewrite-report.md` exists under the artifact root
- **AND** its contents come from the database-backed final outputs layer
