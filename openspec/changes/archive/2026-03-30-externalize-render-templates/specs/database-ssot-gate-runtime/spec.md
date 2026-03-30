## MODIFIED Requirements

### Requirement: Runtime views are render-only

The package MUST render human-readable Markdown views from the DB and MUST NOT treat them as runtime truth.

#### Scenario: A stage write succeeds

- **WHEN** `stage_runtime.py` persists stage data
- **THEN** the runtime view files are re-rendered from the database
- **AND** the render step uses explicit external Jinja2 templates shipped with the package
- **AND** the Agent is expected to treat the rendered files as read-only

### Requirement: Runtime rendering does not silently degrade

The package MUST fail loudly if a required runtime-view template is missing or broken.

#### Scenario: A required runtime-view template is unavailable

- **WHEN** gate or a stage write triggers view rendering
- **AND** a required template file is missing or invalid
- **THEN** the command exits non-zero
- **AND** the runtime does not fall back to inline Python string rendering
