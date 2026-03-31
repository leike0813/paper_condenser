## MODIFIED Requirements

### Requirement: Intermediate runtime views use external render templates

The package MUST keep explicit external templates for all read-only Markdown runtime views. The fixed template-to-view mapping MUST use workflow-aligned numbering rather than historical append order.

#### Scenario: The runtime renders Markdown views

- **WHEN** gate or a stage write triggers view rendering
- **THEN** the Markdown runtime views are rendered from template files in `paper-condenser/assets/render-templates/`
- **AND** the runtime does not assemble those views from hardcoded Python string blocks
- **AND** the template filenames MUST align with the workflow-ordered output filenames:
  - `01-agent-resume.md.j2`
  - `02-manuscript-profile.md.j2`
  - `03-supporting-elements-inventory.md.j2`
  - `04-scope-segments.md.j2`
  - `05-semantic-source-units.md.j2`
  - `06-target-settings.md.j2`
  - `07-content-selection-board.md.j2`
  - `08-style-profile.md.j2`
  - `09-condensation-plan.md.j2`
  - `10-section-rewrite-plan.md.j2`
  - `11-section-drafting-board.md.j2`
