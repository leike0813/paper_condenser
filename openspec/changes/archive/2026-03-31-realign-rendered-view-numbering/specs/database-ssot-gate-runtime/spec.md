## MODIFIED Requirements

### Requirement: Runtime views are render-only

The package MUST render human-readable Markdown views from the DB and MUST NOT treat them as runtime truth. The numbered runtime views MUST be ordered to match the workflow reading order from Stage 1 through Stage 6.

#### Scenario: A stage write succeeds

- **WHEN** `stage_runtime.py` persists stage data
- **THEN** the runtime view files are re-rendered from the database through the external template layer
- **AND** the Agent is expected to treat them as read-only
- **AND** the numbered Markdown view filenames MUST follow the workflow-aligned order:
  - `01-agent-resume.md`
  - `02-manuscript-profile.md`
  - `03-supporting-elements-inventory.md`
  - `04-scope-segments.md`
  - `05-semantic-source-units.md`
  - `06-target-settings.md`
  - `07-content-selection-board.md`
  - `08-style-profile.md`
  - `09-condensation-plan.md`
  - `10-section-rewrite-plan.md`
  - `11-section-drafting-board.md`

#### Scenario: Section drafting state changes

- **WHEN** section drafting, approval, or output-target persistence succeeds
- **THEN** the workflow-aligned drafting-board view and section-review views are re-rendered from the database
- **AND** the Agent is expected to treat them as read-only
