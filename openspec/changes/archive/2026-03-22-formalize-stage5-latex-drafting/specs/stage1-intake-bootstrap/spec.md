## MODIFIED Requirements

### Requirement: Stage 1 Intake Supports Single-File LaTeX Sources

Deterministic Stage 1 intake MUST support UTF-8 single-file LaTeX sources in addition to existing plain-text formats.

#### Scenario: Intake receives a `.tex` manuscript source
- **WHEN** `manuscript-profile.json` records `source_type` as `single_file:tex`
- **THEN** `stage1_intake.py` reads the source text deterministically
- **AND** it writes `content_preview`
- **AND** it writes `source_stats`
- **AND** it updates `intake_status` to `complete`
- **AND** it does not perform semantic LaTeX parsing or interpretation
