## MODIFIED Requirements

### Requirement: `SKILL.md` Must Be Self-Contained For First Read

`paper-condenser/SKILL.md` MUST serve as the primary first-read instruction for the skill.

#### Scenario: Agent enters the skill for the first time

- **WHEN** the Agent reads `SKILL.md`
- **THEN** it MUST be able to understand the skill mission, non-goals, runtime model, and Stage 0-5 workflow without reading any reference document first

### Requirement: `SKILL.md` Must Explain Each Stage In Natural Language

`paper-condenser/SKILL.md` MUST include a concise natural-language overview for every workflow stage from `stage_0_bootstrap` through `stage_5_final_drafting`, plus the completed end-state.

#### Scenario: Agent needs to understand a stage without opening a playbook

- **WHEN** the Agent reads the stage overview in `SKILL.md`
- **THEN** it MUST be able to identify what the stage is for, what work should be done there, what must not be done there, and what counts as done
