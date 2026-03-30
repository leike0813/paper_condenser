## ADDED Requirements

### Requirement: Intermediate runtime views use external render templates

The package MUST keep explicit external templates for all six read-only Markdown runtime views.

#### Scenario: The runtime renders Markdown views

- **WHEN** gate or a stage write triggers view rendering
- **THEN** `01-agent-resume.md` through `06-supporting-elements-inventory.md` are rendered from template files in `paper-condenser/assets/render-templates/`
- **AND** the runtime does not assemble those views from hardcoded Python string blocks

### Requirement: Missing or broken templates fail loudly

The package MUST treat missing render templates or template render failures as hard errors.

#### Scenario: A required template is unavailable

- **WHEN** the runtime attempts to render a read-only Markdown view
- **AND** the corresponding template file is missing or invalid
- **THEN** the command exits non-zero
- **AND** it does not silently fall back to inline Python rendering

## MODIFIED Requirements

### Requirement: Runtime views are render-only

The package MUST render human-readable Markdown views from the DB and MUST NOT treat them as runtime truth.

#### Scenario: A stage write succeeds

- **WHEN** `stage_runtime.py` persists stage data
- **THEN** the runtime view files are re-rendered from the database through the external template layer
- **AND** the Agent is expected to treat them as read-only
