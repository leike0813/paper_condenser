## ADDED Requirements

### Requirement: Scope segmentation is persisted before section-level drafting

The runtime MUST persist deterministic scope segments after manuscript analysis and before section rewrite planning.

#### Scenario: Scope segmentation is required

- **WHEN** manuscript analysis has completed and the scope is machine-readable
- **THEN** gate returns `persist_scope_segments`
- **AND** paragraph-level scope segments are persisted into the runtime DB
- **AND** figure, table, and display blocks remain standalone segments

### Requirement: Section drafting is gate-driven

The runtime MUST draft final outputs section by section under explicit gating and approval.

#### Scenario: A section draft is written

- **WHEN** the active section draft is persisted
- **THEN** the runtime validates the section count against the planned count
- **AND** it renders a section review artifact
- **AND** it blocks on section approval before activating the next section

### Requirement: Final bundle rendering happens only after all section approvals

The runtime MUST wait until every section is approved and the output target is confirmed before rendering final outputs.

#### Scenario: Final outputs are rendered

- **WHEN** all section drafts are approved and the output target is confirmed
- **THEN** gate returns `render_final_output_bundle`
- **AND** the runtime renders `final-draft.tex` and `rewrite-report.md`
- **AND** it copies referenced images into the output directory's `images/` subdirectory
- **AND** it rewrites LaTeX image paths to the copied locations
