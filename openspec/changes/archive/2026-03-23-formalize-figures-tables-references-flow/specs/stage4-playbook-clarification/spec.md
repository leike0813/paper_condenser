## MODIFIED Requirements

### Requirement: Stage 4 Plans Supporting-Elements Migration

Stage 4 MUST explicitly plan how figures, tables, and references will be handled in the condensed manuscript.

#### Scenario: Stage 4 planning is inspected
- **WHEN** `condensation-plan.md` is reviewed
- **THEN** it contains figure/table migration decisions
- **AND** it contains reference migration decisions
- **AND** those decisions are part of the approval bundle

### Requirement: Stage 4 Approval Gate Includes Supporting-Elements Decisions

Stage 4 MUST NOT complete without approved supporting-elements decisions.

#### Scenario: The workflow checks whether Stage 5 may begin
- **WHEN** Stage 4 is evaluated for completion
- **THEN** the figure/table plan is non-empty
- **AND** the reference plan is non-empty
- **AND** `Approval` records `Status: approved`
