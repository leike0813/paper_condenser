## MODIFIED Requirements

### Requirement: Stage 2 Captures Supporting-Elements Preferences

Stage 2 MUST capture and confirm user preferences for figure/table handling and reference handling.

#### Scenario: Stage 2 target settings are collected
- **WHEN** the agent gathers confirmed target settings
- **THEN** it includes figure/table handling preference
- **AND** it includes reference-handling preference
- **AND** both preferences are covered by the Stage 2 readback

### Requirement: Stage 2 Confirmation Bundle Includes Supporting-Elements Preferences

The Stage 2 completion gate MUST include confirmed supporting-elements preferences.

#### Scenario: Stage 2 is evaluated for completion
- **WHEN** the workflow checks whether Stage 3 may begin
- **THEN** the supporting-elements preference fields are non-empty
- **AND** `user_confirmed=true`
