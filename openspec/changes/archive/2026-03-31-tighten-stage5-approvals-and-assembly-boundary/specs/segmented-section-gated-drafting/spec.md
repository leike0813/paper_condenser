## MODIFIED Requirements

### Requirement: Stage 6 starts only after Stage 5 plans are approved

Section drafting MUST remain blocked until both the overall condensation plan and the detailed section rewrite plan are explicitly approved.

#### Scenario: Section drafting is requested too early

- **WHEN** the overall plan is unapproved or the section rewrite plan is unapproved
- **THEN** gate MUST NOT return `prepare_section_drafting`
- **AND** it MUST return the relevant Stage 5 confirm action instead

### Requirement: Final bundle rendering is assembly-only

The final bundle render step MUST assemble approved section drafts without performing additional free-form rewriting.

#### Scenario: Final outputs are rendered

- **WHEN** `render_final_output_bundle` runs
- **THEN** it assembles approved section drafts in order
- **AND** it MUST NOT introduce new section-level prose that was not already present in approved drafts
