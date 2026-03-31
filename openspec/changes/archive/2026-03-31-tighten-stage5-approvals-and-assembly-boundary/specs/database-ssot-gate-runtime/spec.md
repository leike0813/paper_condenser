## MODIFIED Requirements

### Requirement: Gate discipline blocks premature drafting

The runtime gate MUST keep Stage 5 planning and Stage 6 drafting as separate gated phases.

#### Scenario: Stage 5 has not fully completed

- **WHEN** the condensation plan or section rewrite plan is still waiting for approval
- **THEN** gate returns the corresponding confirm action
- **AND** it MUST NOT advance to Stage 6 drafting actions

### Requirement: Final outputs are rendered by assembly from DB-backed approved drafts

The runtime MUST treat final bundle rendering as an assembly step over DB-backed approved drafts.

#### Scenario: Final bundle rendering completes

- **WHEN** `render_final_output_bundle` succeeds
- **THEN** the DB-backed final outputs are rendered from approved section drafts
- **AND** the runtime copies any referenced images into the output directory
- **AND** the runtime rewrites image paths in the final LaTeX output
