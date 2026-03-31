## MODIFIED Requirements

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

### Requirement: Section rewrite plan previews final manuscript shape

The detailed section rewrite plan MUST be rich enough for the user to preview the intended final manuscript shape.

#### Scenario: Section rewrite plan is rendered

- **WHEN** `09-section-rewrite-plan.md` is rendered
- **THEN** each section entry includes a section summary
- **AND** it includes section strategy
- **AND** it includes figure/table usage strategy
- **AND** it includes reference usage strategy
- **AND** it makes aux-backed usage visible when applicable
