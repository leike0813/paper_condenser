## Purpose

Define `SKILL.md` as the primary self-contained instruction and references as on-demand supplements.
## Requirements
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

### Requirement: References Must Be Explicitly On-Demand

`paper-condenser/SKILL.md` MUST explicitly state that `references/` documents are supplementary and should be loaded on demand.

#### Scenario: Agent resumes after a long context

- **WHEN** the Agent resumes execution from a gate result
- **THEN** it is instructed to read the gate-provided `runtime_digest` first
- **AND** then to inspect `next_action` and `next_action_payload_example`
- **AND** only then to load stage references on demand if needed

### Requirement: Reference Index Must Be Need-Oriented

The references section in `paper-condenser/SKILL.md` MUST describe when to read each referenced document, not just list file names.

#### Scenario: Agent encounters a specific need

- **WHEN** the Agent needs runtime CLI details, DB/view semantics, or stage-specific execution rules
- **THEN** `SKILL.md` MUST point it to the corresponding supplemental document

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

### Requirement: SKILL.md Explains Language Context And Final Translation

`SKILL.md` MUST explain that:

- Stage 2 confirms `working_language`
- runtime text artifacts and section drafts use `working_language`
- Stage 3 finalizes `target_language`
- final drafting includes an explicit translation step before assembly-only rendering

#### Scenario: Agent reads only SKILL.md

- **WHEN** an agent reads `SKILL.md` without opening playbooks
- **THEN** it can understand the working-vs-target language split
- **AND** it can see that final assembly does not perform freeform rewriting

