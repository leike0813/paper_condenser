## ADDED Requirements

### Requirement: `SKILL.md` stays concise and payload-light

`paper-condenser/SKILL.md` MUST remain a self-contained first-read instruction, but it MUST NOT serve as the detailed payload schema reference.

#### Scenario: Agent reads the skill for the first time

- **WHEN** the Agent reads `SKILL.md`
- **THEN** it can understand the mission, runtime model, Stage 0-6 workflow, and action meanings
- **AND** it is instructed to get payload details from gate output or stage playbooks rather than from large payload field inventories in `SKILL.md`

### Requirement: `SKILL.md` remains compact

`paper-condenser/SKILL.md` MUST stay under 500 lines after the compression refactor.

#### Scenario: The file is checked after refactor

- **WHEN** line count is measured
- **THEN** `SKILL.md` is fewer than 500 lines long
