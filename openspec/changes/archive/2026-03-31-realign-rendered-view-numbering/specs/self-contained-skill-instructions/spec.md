## MODIFIED Requirements

### Requirement: `SKILL.md` Must Be Self-Contained For First Read

`paper-condenser/SKILL.md` MUST serve as the primary first-read instruction for the skill, and its rendered-view inventory MUST use the workflow-aligned numbering used by the runtime.

#### Scenario: Agent enters the skill for the first time

- **WHEN** the Agent reads `SKILL.md`
- **THEN** it MUST be able to understand the skill mission, non-goals, runtime model, and Stage 0-6 workflow without reading any reference document first
- **AND** any rendered-view list shown in `SKILL.md` MUST use the workflow-aligned filenames:
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
