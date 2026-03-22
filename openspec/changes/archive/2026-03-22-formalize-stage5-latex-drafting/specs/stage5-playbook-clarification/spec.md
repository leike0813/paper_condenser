## ADDED Requirements

### Requirement: Explicit Stage 5 LaTeX Drafting Sequence

Stage 5 MUST define an explicit LaTeX drafting sequence instead of treating final writing as a single opaque step.

#### Scenario: The Stage 5 playbook is inspected
- **WHEN** the Stage 5 instructions are read
- **THEN** they define drafting preflight
- **AND** they define helper-script-based final-draft initialization
- **AND** they define final-draft initialization from a selected preset template
- **AND** they define section-by-section drafting
- **AND** they define whole-draft integration
- **AND** they define whole-draft review
- **AND** they define fallback decisions when upstream gaps are discovered

### Requirement: Stage 5 Uses A Minimal Deterministic Helper For Preflight

The package MUST provide a minimal deterministic helper for Stage 5 preflight and final-draft skeleton initialization.

#### Scenario: Stage 5 is about to begin
- **WHEN** the workflow reaches Stage 5
- **THEN** a helper script validates the required core artifacts
- **AND** it checks that `target-settings.json` is confirmed
- **AND** it checks that `target-settings.json.latex_template_id` is non-empty
- **AND** it checks that `condensation-plan.md` records `Status: approved`
- **AND** it initializes `final-draft.tex` from the selected preset without generating manuscript prose

### Requirement: Final Draft Must Be Persisted As LaTeX Runtime Truth

The package MUST define a persisted LaTeX file as the formal runtime truth for final drafting output.

#### Scenario: The final drafting output is reviewed
- **WHEN** Stage 5 output is inspected
- **THEN** the runtime truth is `artifacts/<document-slug>/final-draft.tex`
- **AND** the package does not treat the chat response alone as the authoritative final draft

### Requirement: Stage 5 Requires Approved Upstream Inputs

Stage 5 MUST remain gated by the four core artifacts plus explicit template selection and Stage 4 approval.

#### Scenario: The workflow checks whether Stage 5 may begin
- **WHEN** Stage 5 preflight is evaluated
- **THEN** the four core artifacts are present
- **AND** `target-settings.json` is confirmed
- **AND** `target-settings.json.latex_template_id` is non-empty
- **AND** `condensation-plan.md` records `Status: approved`

### Requirement: Stage 5 Must Support Controlled Fallback

Stage 5 MUST define a fallback rule for unresolved upstream gaps instead of drafting through them silently.

#### Scenario: Drafting reveals an upstream gap
- **WHEN** Stage 5 discovers that understanding, target settings, style guidance, or the condensation plan is incomplete or contradictory
- **THEN** the workflow pauses final drafting
- **AND** it routes the task back to the corresponding earlier stage
- **AND** it does not treat the current draft as final until the gap is resolved
