## ADDED Requirements

### Requirement: Explicit Stage 3 Style-Analysis Sequence

Stage 3 MUST define an explicit sequence for building a usable style profile.

#### Scenario: The Stage 3 playbook is inspected
- **WHEN** the Stage 3 instructions are read
- **THEN** they define source-style observation
- **AND** they define problem diagnosis
- **AND** they define target style guidance synthesis
- **AND** they define open-question consolidation

### Requirement: Existing Style Profile Structure Remains Authoritative

The package MUST represent Stage 3 output using the existing `style-profile.md` structure.

#### Scenario: Stage 3 output is reviewed
- **WHEN** `style-profile.md` is inspected
- **THEN** it uses `Source Style`
- **AND** it uses `Problems To Fix`
- **AND** it uses `Target Style Guidance`
- **AND** it uses `Open Questions`
- **AND** the package does not introduce new Stage 3 status fields or status sections

### Requirement: Style Analysis Must Be Persisted During Stage 3

Stage 3 MUST persist style-analysis results into `style-profile.md` instead of keeping them only in the live conversation.

#### Scenario: Stage 3 analysis progresses
- **WHEN** the agent identifies source-style traits, style problems, target guidance, or unresolved style questions
- **THEN** it writes the corresponding content into the appropriate section of `style-profile.md`

### Requirement: Stage 3 Completion Gate

The package MUST define a specific minimum gate for entering Stage 4.

#### Scenario: The workflow checks whether Stage 4 may begin
- **WHEN** Stage 3 is evaluated for completion
- **THEN** `Source Style` contains usable style observations
- **AND** `Problems To Fix` contains explicit issues to correct
- **AND** `Target Style Guidance` contains actionable writing guidance
- **AND** `Open Questions` explicitly records unresolved style preferences or remains as an explicit section when no unresolved questions remain

### Requirement: Stage 3 Question Boundary

Stage 3 MUST remain limited to style analysis and style-preference clarification.

#### Scenario: The agent asks Stage 3 questions
- **WHEN** the Stage 3 interaction is in progress
- **THEN** the questions are limited to style preference, tone boundary, expression preference, and style-level correction decisions
- **AND** the agent does not start Stage 4 priority, outline, or length-allocation negotiation

### Requirement: Stage 3 May Carry Forward Unresolved Style Questions

The package MUST allow Stage 3 to complete with unresolved but explicit style questions.

#### Scenario: Style analysis is usable but some preferences remain unresolved
- **WHEN** Stage 3 has produced actionable guidance but still has non-blocking style ambiguities
- **THEN** those ambiguities are written into `Open Questions`
- **AND** the workflow may still advance if the rest of the Stage 3 gate is satisfied
