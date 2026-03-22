## ADDED Requirements

### Requirement: Stage 5 Must Persist A Rewrite Report

The package MUST produce a persisted rewrite report after final drafting.

#### Scenario: Stage 5 completes successfully
- **WHEN** the workflow finishes final drafting
- **THEN** `.paper-condenser-tmp/<document-slug>/rewrite-report.md` exists
- **AND** the report is treated as a required Stage 5 output rather than an optional note

### Requirement: Rewrite Report Uses Mixed-Granularity Traceability

The rewrite report MUST provide both broad and selective fine-grained source mapping.

#### Scenario: The rewrite report is inspected
- **WHEN** `rewrite-report.md` is reviewed
- **THEN** every final section or subsection has a section-level source mapping
- **AND** key paragraphs, key figures, key tables, or key references can receive more detailed notes
- **AND** the report does not require paragraph-level mapping for every paragraph

### Requirement: Rewrite Report Summarizes The Transformation Process

The rewrite report MUST summarize the decisions that shaped the final condensed manuscript.

#### Scenario: A user reads the report to continue revision
- **WHEN** `rewrite-report.md` is reviewed
- **THEN** it summarizes the key Stage 1-4 decisions that materially shaped the final draft
- **AND** it records unresolved risks or follow-up items for later revision

### Requirement: Markdown Structure Is Stable

The rewrite report MUST use a stable Markdown structure.

#### Scenario: The rewrite report format is reviewed
- **WHEN** `rewrite-report.md` is inspected
- **THEN** it contains `Run Summary`
- **AND** it contains `Stage Decisions`
- **AND** it contains `Final Draft Section Map`
- **AND** it contains `Key Paragraph And Element Notes`
- **AND** it contains `Unresolved Risks / Follow-up`
