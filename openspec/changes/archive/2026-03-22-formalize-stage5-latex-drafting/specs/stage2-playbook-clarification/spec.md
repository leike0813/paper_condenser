## MODIFIED Requirements

### Requirement: Stage 2 Includes LaTeX Template Selection

Stage 2 MUST treat LaTeX preset selection as part of the confirmed target-setting bundle.

#### Scenario: The Stage 2 playbook is inspected
- **WHEN** the Stage 2 instructions are read
- **THEN** they define `latex_template_id` collection
- **AND** they include template selection in the full readback
- **AND** they require explicit confirmation before Stage 2 is considered complete

### Requirement: Template Choice Uses Existing Target-Settings Artifact

The package MUST store the selected LaTeX preset inside `target-settings.json` rather than in a separate artifact.

#### Scenario: Stage 2 output is reviewed
- **WHEN** `target-settings.json` is inspected
- **THEN** it contains `latex_template_id`
- **AND** `user_confirmed` remains `false` until the template choice is confirmed together with the rest of the target-setting bundle
