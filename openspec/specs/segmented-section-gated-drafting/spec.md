## Purpose

Define section-loop drafting, section approval, and final bundle rendering constraints.
## Requirements
### Requirement: Section drafting is gate-driven

The runtime MUST draft final outputs section by section under explicit gating and approval.

#### Scenario: A section draft is written

- **WHEN** the active section draft is persisted
- **THEN** the runtime validates the section count against the planned count
- **AND** it renders a section review artifact
- **AND** it blocks on section approval before activating the next section

### Requirement: Stage 6 starts only after Stage 5 plans are approved

Section drafting MUST remain blocked until both the overall condensation plan and the detailed section rewrite plan are explicitly approved.

#### Scenario: Section drafting is requested too early

- **WHEN** the overall plan is unapproved or the section rewrite plan is unapproved
- **THEN** gate MUST NOT return `prepare_section_drafting`
- **AND** it MUST return the relevant Stage 5 confirm action instead

### Requirement: Final bundle rendering happens only after all section approvals

The runtime MUST wait until every section is approved and the output target is confirmed before rendering final outputs.

#### Scenario: Final outputs are rendered

- **WHEN** all section drafts are approved and the output target is confirmed
- **THEN** gate returns `render_final_output_bundle`
- **AND** the runtime renders `final-draft.tex` and `rewrite-report.md`
- **AND** it copies referenced images into the output directory's `images/` subdirectory
- **AND** it rewrites LaTeX image paths to the copied locations

### Requirement: Final bundle rendering is assembly-only

The final bundle render step MUST assemble approved section drafts without performing additional free-form rewriting.

#### Scenario: Final outputs are rendered

- **WHEN** `render_final_output_bundle` runs
- **THEN** it assembles approved section drafts in order
- **AND** it MUST NOT introduce new section-level prose that was not already present in approved drafts

