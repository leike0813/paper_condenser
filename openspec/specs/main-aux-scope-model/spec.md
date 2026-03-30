## Purpose

Define the main/aux scope model for Stage 2 analysis and provenance.

## Requirements

### Requirement: Stage 2 supports one main scope plus zero-to-many aux scopes

The runtime MUST persist manuscript analysis using a main/aux scope model rather than a single scope field.

#### Scenario: Stage 2 analysis is written

- **WHEN** `persist_manuscript_analysis` succeeds
- **THEN** the runtime stores `main_scope`, `main_scope_locator`, and `aux_scopes`
- **AND** aux scopes are treated as support-only ranges rather than a second main target

### Requirement: Raw segmentation preserves main and aux role metadata

The runtime MUST keep raw segmentation in one table and record where each raw block came from.

#### Scenario: Raw scope segments are persisted

- **WHEN** `persist_raw_scope_segments` succeeds
- **THEN** each raw segment row stores `scope_role`, `scope_bucket_id`, and `scope_label`
- **AND** rows from main and aux ranges are globally ordered by source position

### Requirement: Downstream writing exposes main and aux provenance

The runtime MUST let downstream planning and review distinguish between main and aux support.

#### Scenario: A section plan or section review references a semantic unit

- **WHEN** a semantic unit contains aux-backed raw members
- **THEN** rendered views expose the unit's main/aux composition
- **AND** section planning records why aux support is being used
