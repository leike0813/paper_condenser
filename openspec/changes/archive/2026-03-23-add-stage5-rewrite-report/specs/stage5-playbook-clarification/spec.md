## MODIFIED Requirements

### Requirement: Stage 5 Includes Rewrite-Report Generation

Stage 5 MUST include a dedicated rewrite-report generation step after drafting and before final completion.

#### Scenario: The Stage 5 playbook is inspected
- **WHEN** the Stage 5 instructions are read
- **THEN** they define final-draft generation
- **AND** they define rewrite-report generation
- **AND** they define review of both outputs before completion

### Requirement: Stage 5 Completion Gate Covers Both Outputs

Stage 5 MUST NOT complete with only the final LaTeX manuscript.

#### Scenario: The workflow checks whether Stage 5 is complete
- **WHEN** final delivery is evaluated
- **THEN** `final-draft.tex` exists
- **AND** `rewrite-report.md` exists
- **AND** both outputs satisfy the documented Stage 5 gate
