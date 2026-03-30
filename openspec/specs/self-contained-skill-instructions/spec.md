## Purpose

Define `SKILL.md` as the primary self-contained instruction and references as on-demand supplements.

## Requirements

### Requirement: `SKILL.md` Must Be Self-Contained For First Read

`paper-condenser/SKILL.md` MUST serve as the primary first-read instruction for the skill.

#### Scenario: Agent enters the skill for the first time

- **WHEN** the Agent reads `SKILL.md`
- **THEN** it MUST be able to understand the skill mission, non-goals, runtime model, and Stage 0-6 workflow without reading any reference document first

### Requirement: `SKILL.md` Must Explain Each Stage In Natural Language

`paper-condenser/SKILL.md` MUST include a concise natural-language overview for every workflow stage from `stage_0_bootstrap` through `stage_6_final_drafting`.

#### Scenario: Agent needs to understand a stage without opening a playbook

- **WHEN** the Agent reads the stage overview in `SKILL.md`
- **THEN** it MUST be able to identify what the stage is for, what work should be done there, what must not be done there, and what counts as done

### Requirement: References Must Be Explicitly On-Demand

`paper-condenser/SKILL.md` MUST explicitly state that `references/` documents are supplementary and should be loaded on demand.

#### Scenario: Agent starts a task

- **WHEN** the Agent begins execution
- **THEN** it MUST be instructed to read `SKILL.md` first
- **AND** it MUST be instructed not to bulk-read all documents in `references/`
- **AND** it MUST be given guidance about which reference to load for which kind of difficulty or uncertainty

### Requirement: Reference Index Must Be Need-Oriented

The references section in `paper-condenser/SKILL.md` MUST describe when to read each referenced document, not just list file names.

#### Scenario: Agent encounters a specific need

- **WHEN** the Agent needs runtime CLI details, DB/view semantics, or stage-specific execution rules
- **THEN** `SKILL.md` MUST point it to the corresponding supplemental document
