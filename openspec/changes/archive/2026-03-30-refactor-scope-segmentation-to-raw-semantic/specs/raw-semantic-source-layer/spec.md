## ADDED Requirements

### Requirement: Stage 2 separates raw segmentation from semantic consolidation

The runtime MUST treat deterministic scope segmentation and semantic source-unit consolidation as two different actions.

#### Scenario: Stage 2 proceeds after manuscript analysis

- **WHEN** manuscript analysis is complete
- **THEN** gate returns `persist_raw_scope_segments`
- **AND** after raw segments are persisted, gate returns `persist_semantic_source_units`
- **AND** downstream stages remain blocked until semantic source units are present

### Requirement: Raw scope segments are facts, not final writing units

The runtime MUST treat raw scope segments as deterministic facts only.

#### Scenario: A raw segmentation exists

- **WHEN** `persist_raw_scope_segments` succeeds
- **THEN** the DB stores paragraph / figure / table / display-block raw segments
- **AND** those rows are not treated as the final source layer for section rewrite planning

### Requirement: Section rewrite planning uses semantic source units

The runtime MUST use semantic source units as the primary provenance path for section rewrite plans and section drafts.

#### Scenario: A section rewrite plan is persisted

- **WHEN** `persist_section_rewrite_plan` writes section-level plan rows
- **THEN** the primary source bindings reference semantic units
- **AND** Stage 6 draft provenance also binds to semantic units rather than raw segments
