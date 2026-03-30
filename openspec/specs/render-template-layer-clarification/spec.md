## Purpose

Define the external template layer for render-only Markdown runtime views.

## Requirements

### Requirement: Intermediate runtime views use external render templates

The package MUST keep explicit external templates for all read-only Markdown runtime views.

#### Scenario: The runtime renders Markdown views

- **WHEN** gate or a stage write triggers view rendering
- **THEN** the Markdown runtime views are rendered from template files in `paper-condenser/assets/render-templates/`
- **AND** the runtime does not assemble those views from hardcoded Python string blocks

### Requirement: Missing or broken templates fail loudly

The package MUST treat missing render templates or template render failures as hard errors.

#### Scenario: A required template is unavailable

- **WHEN** the runtime attempts to render a read-only Markdown view
- **AND** the corresponding template file is missing or invalid
- **THEN** the command exits non-zero
- **AND** it does not silently fall back to inline Python rendering
