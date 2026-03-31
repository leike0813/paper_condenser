## MODIFIED Requirements

### Requirement: Stage 4 planning must finish before Stage 5 drafting

The skill MUST complete and approve both layers of planning before final drafting begins.

#### Scenario: Section rewrite plan is approved

- **WHEN** the section rewrite plan has been approved
- **THEN** gate may advance to `stage_5_final_drafting`
- **AND** Stage 5 drafting may start only after Stage 4 planning is complete

#### Scenario: Final outputs are completed

- **WHEN** the runtime reaches `stage_6_completed`
- **THEN** both rendered files already exist
- **AND** the drafting loop no longer accepts new stage writes
