## MODIFIED Requirements

### Requirement: Stage 5 Respects Approved Supporting-Elements Decisions

Stage 5 MUST draft the final LaTeX output in a way that follows approved figure/table/reference decisions.

#### Scenario: Stage 5 drafting is reviewed
- **WHEN** the final-draft workflow is read
- **THEN** it checks the approved supporting-elements plan before migration
- **AND** it preserves, rewrites, or placeholders supporting elements according to that plan

### Requirement: Stage 5 Review Covers Supporting Elements

Stage 5 whole-draft review MUST include supporting-elements checks.

#### Scenario: Stage 5 whole-draft review runs
- **WHEN** the agent reviews `final-draft.tex`
- **THEN** it checks that required figures and tables were not silently dropped
- **AND** it checks that required citations and bibliography structure are still represented
