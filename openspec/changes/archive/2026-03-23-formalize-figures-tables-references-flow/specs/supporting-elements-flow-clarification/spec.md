## ADDED Requirements

### Requirement: Supporting Elements Flow Exists

The package MUST define a dedicated handling flow for figures, tables, citations, and bibliography structure.

#### Scenario: The package workflow is inspected
- **WHEN** the skill contract is read
- **THEN** it defines how supporting elements are handled in Stage 1
- **AND** it defines how supporting elements are planned in Stage 4
- **AND** it defines how supporting elements are migrated in Stage 5

### Requirement: Deterministic Supporting-Elements Inventory

The package MUST provide a deterministic helper script that extracts supporting-elements inventory from a single-file `.tex` manuscript.

#### Scenario: The supporting-elements helper is inspected
- **WHEN** the package scripts are reviewed
- **THEN** a formal helper entrypoint exists for extracting figure, table, citation, and bibliography inventory
- **AND** the helper operates on `--artifact-root <path>`
- **AND** the helper writes deterministic facts into `manuscript-profile.json`

### Requirement: Four Existing Truth Sources Remain Authoritative

The package MUST NOT introduce a fifth intermediate artifact for supporting elements.

#### Scenario: Supporting-elements persistence is reviewed
- **WHEN** the package artifacts are inspected
- **THEN** supporting-elements facts are stored in `manuscript-profile.json`
- **AND** target preferences are stored in `target-settings.json`
- **AND** migration decisions are stored in `condensation-plan.md`
- **AND** style guidance remains in `style-profile.md`

### Requirement: Supporting Elements Must Not Be Silently Dropped

The package MUST prevent silent loss of approved figures, tables, or references during Stage 5.

#### Scenario: Stage 5 produces a final draft
- **WHEN** the final LaTeX draft is generated
- **THEN** approved supporting elements are either migrated or explicitly represented with a clear placeholder
- **AND** the workflow does not silently omit them
