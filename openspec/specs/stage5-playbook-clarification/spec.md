## Purpose

Define Stage 5 final drafting and the final drafting output path after the DB-backed runtime refactor.
## Requirements
### Requirement: Stage 5 is DB-backed and gated

Stage 5 MUST persist final drafting results to SQLite and MUST render final outputs from DB state.

#### Scenario: Final drafting is completed

- **WHEN** final bundle rendering succeeds
- **THEN** the DB stores the final draft and rewrite report content
- **AND** the runtime renders `final-draft.tex` and `rewrite-report.md`
- **AND** the workflow may only reach `stage_6_completed` after both rendered files exist

### Requirement: Stage 5 uses two layers of planning and two explicit approvals

Stage 5 MUST require explicit user approval for both the overall condensation plan and the detailed section rewrite plan before final drafting may begin.

#### Scenario: Overall condensation plan is drafted

- **WHEN** `persist_condensation_plan` succeeds
- **THEN** gate returns `confirm_condensation_plan`
- **AND** the runtime MUST NOT allow `persist_section_rewrite_plan` until the overall plan is approved

#### Scenario: Section rewrite plan is drafted

- **WHEN** `persist_section_rewrite_plan` succeeds
- **THEN** gate returns `confirm_section_rewrite_plan`
- **AND** the runtime MUST NOT allow Stage 6 drafting until the section rewrite plan is approved

### Requirement: Stage 4 planning must finish before Stage 5 drafting

The skill MUST complete and approve both layers of planning before final drafting begins.

#### Scenario: Section rewrite plan is approved

- **WHEN** the section rewrite plan has been approved
- **THEN** gate may advance to `stage_5_final_drafting`
- **AND** Stage 5 drafting may start only after Stage 4 planning is complete

#### Scenario: Final outputs are completed

- **WHEN** the runtime reaches `stage_6_completed`
- **THEN** both rendered files already exist
- **AND** the drafting loop no longer accepts new stage writes

### Requirement: Section rewrite plan previews final manuscript shape

The detailed section rewrite plan MUST be rich enough for the user to preview the intended final manuscript shape.

#### Scenario: Section rewrite plan is rendered

- **WHEN** `09-section-rewrite-plan.md` is rendered
- **THEN** each section entry includes a section summary
- **AND** it includes section strategy
- **AND** it includes figure/table usage strategy
- **AND** it includes reference usage strategy
- **AND** it makes aux-backed usage visible when applicable

