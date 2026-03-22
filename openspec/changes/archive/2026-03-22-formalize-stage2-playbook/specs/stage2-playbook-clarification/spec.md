## ADDED Requirements

### Requirement: Explicit Stage 2 Target-Setting Sequence

Stage 2 MUST define an explicit sequence for collecting and locking target settings.

#### Scenario: The Stage 2 playbook is inspected
- **WHEN** the Stage 2 instructions are read
- **THEN** they define target language collection
- **AND** they define target form collection
- **AND** they define target journal type collection
- **AND** they define target body length collection
- **AND** they define must-keep collection
- **AND** they define must-avoid collection
- **AND** they define a full readback before confirmation

### Requirement: Draft State Uses Existing Fields

The package MUST represent Stage 2 draft progress without expanding the `target-settings.json` schema.

#### Scenario: Stage 2 is still in progress
- **WHEN** the user has not yet explicitly confirmed the full target-setting bundle
- **THEN** `target-settings.json` may be partially filled
- **AND** `user_confirmed` remains `false`
- **AND** the package does not introduce additional Stage 2 status fields

### Requirement: Target Settings Must Be Persisted During Collection

Stage 2 MUST persist partial target-setting results into `target-settings.json` instead of keeping them only in the live conversation.

#### Scenario: A Stage 2 answer is collected
- **WHEN** the user answers one or more Stage 2 questions
- **THEN** the corresponding fields in `target-settings.json` are updated
- **AND** the workflow may continue collecting the remaining settings while `user_confirmed` is still `false`

### Requirement: Confirmation Requires Full Readback

Stage 2 MUST require a readback of the full setting bundle before final confirmation.

#### Scenario: The workflow is about to mark target settings as confirmed
- **WHEN** all core Stage 2 fields and the keep/avoid constraints have been collected
- **THEN** the agent presents the full setting bundle back to the user
- **AND** it only sets `user_confirmed` to `true` after explicit user confirmation

### Requirement: Stage 2 Completion Gate

The package MUST define a specific minimum gate for entering Stage 3.

#### Scenario: The workflow checks whether Stage 3 may begin
- **WHEN** Stage 2 is evaluated for completion
- **THEN** `target_language` is non-empty
- **AND** `target_form` is non-empty
- **AND** `target_journal_type` is non-empty
- **AND** `target_body_length.value` and `target_body_length.unit` are populated
- **AND** `must_keep` is populated
- **AND** `must_avoid` is populated
- **AND** `user_confirmed` is `true`

### Requirement: Stage 2 Question Boundary

Stage 2 MUST remain limited to target-setting and keep/avoid constraints.

#### Scenario: The agent asks Stage 2 questions
- **WHEN** the Stage 2 interaction is in progress
- **THEN** the questions are limited to target language, target form, target journal type, target body length, must-keep, and must-avoid constraints
- **AND** the agent does not start Stage 3 style diagnosis
- **AND** the agent does not start Stage 4 outline, priority, or condensation-plan negotiation
