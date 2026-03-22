## MODIFIED Requirements

### Requirement: Stage 1 Includes Supporting-Elements Inventory

Stage 1 MUST include deterministic extraction of figures, tables, citations, and bibliography structure before semantic understanding may complete.

#### Scenario: Stage 1 is executed
- **WHEN** Stage 1 begins semantic manuscript understanding
- **THEN** `stage1_intake.py` has already completed
- **AND** the supporting-elements extraction helper has already completed
- **AND** `manuscript-profile.json` contains persisted supporting-elements facts

### Requirement: Stage 1 Completion Gate Covers Supporting Elements

Stage 1 MUST NOT complete without a persisted supporting-elements inventory.

#### Scenario: Stage 1 is evaluated for completion
- **WHEN** the workflow checks whether Stage 2 may begin
- **THEN** `supporting_elements_status` is complete
- **AND** figures, tables, citations, and bibliography structure have been inventoried as facts
