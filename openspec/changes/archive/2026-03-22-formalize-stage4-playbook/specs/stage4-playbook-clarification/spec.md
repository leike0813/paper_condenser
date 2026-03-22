## ADDED Requirements

### Requirement: Explicit Stage 4 Planning Sequence

Stage 4 MUST define an explicit sequence for building an approved condensation plan.

#### Scenario: The Stage 4 playbook is inspected
- **WHEN** the Stage 4 instructions are read
- **THEN** they define core-message consolidation
- **AND** they define priority mapping
- **AND** they define target-outline planning
- **AND** they define length allocation
- **AND** they define omit/merge strategy planning
- **AND** they define approval capture

### Requirement: Existing Condensation Plan Structure Remains Authoritative

The package MUST represent Stage 4 output using the existing `condensation-plan.md` structure.

#### Scenario: Stage 4 output is reviewed
- **WHEN** `condensation-plan.md` is inspected
- **THEN** it uses `Core Message`
- **AND** it uses `Priority Map`
- **AND** it uses `Target Outline`
- **AND** it uses `Length Allocation`
- **AND** it uses `Omit / Merge Strategy`
- **AND** it uses `Approval`
- **AND** the package does not introduce new Stage 4 status fields

### Requirement: Condensation Planning Must Be Persisted During Stage 4

Stage 4 MUST persist planning results into `condensation-plan.md` instead of keeping them only in the live conversation.

#### Scenario: Stage 4 planning progresses
- **WHEN** the agent identifies core message, priorities, outline, length allocation, omit/merge strategy, or approval status
- **THEN** it writes the corresponding content into the appropriate section of `condensation-plan.md`

### Requirement: Approval Uses Existing Status Line

The package MUST keep using the existing `Approval` status line as the only explicit approval marker.

#### Scenario: Stage 4 approval state is reviewed
- **WHEN** `condensation-plan.md` is inspected
- **THEN** approval is recorded through `Status: not approved|approved`
- **AND** the package does not introduce additional approval fields or status blocks

### Requirement: Stage 4 Completion Gate

The package MUST define a specific minimum gate for entering Stage 5.

#### Scenario: The workflow checks whether Stage 5 may begin
- **WHEN** Stage 4 is evaluated for completion
- **THEN** `Core Message` contains the must-retain core message
- **AND** `Priority Map` contains explicit priority decisions
- **AND** `Target Outline` contains the target manuscript outline
- **AND** `Length Allocation` contains section-level allocation guidance
- **AND** `Omit / Merge Strategy` contains explicit compression strategy
- **AND** `Approval` records `Status: approved`

### Requirement: Stage 4 Question Boundary

Stage 4 MUST remain limited to condensation-plan convergence and approval.

#### Scenario: The agent asks Stage 4 questions
- **WHEN** the Stage 4 interaction is in progress
- **THEN** the questions are limited to core message, priority, outline, length allocation, omit/merge strategy, and approval
- **AND** the agent does not start final drafting before approval is recorded
