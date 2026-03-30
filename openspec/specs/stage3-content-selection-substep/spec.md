## Purpose

Define the dedicated content-selection substep inside Stage 3 target settings.

## Requirements

### Requirement: Stage 3 includes a dedicated content-selection substep

The runtime MUST treat Stage 3 target setting and Stage 3 content-selection confirmation as separate gated actions.

#### Scenario: Stage 3 basics are complete

- **WHEN** basic target settings are persisted
- **THEN** gate returns `persist_content_selection_board`
- **AND** the runtime does not allow Stage 4 until content selection is confirmed

### Requirement: Content-selection items are semantic aggregations

The content-selection board MUST be built from semantic source units rather than direct raw-segment mappings.

#### Scenario: A board item is rendered

- **WHEN** a content-selection item is shown in the rendered board
- **THEN** it includes its semantic-unit bindings
- **AND** the user can see the underlying raw-member provenance through those semantic units

### Requirement: Stage 5 consumes keep / simplify / avoid constraints

The section rewrite plan MUST consume the confirmed Stage 3 triad.

#### Scenario: Stage 3 confirms simplify-first items

- **WHEN** `target_settings.simplify_first` contains confirmed items
- **THEN** Stage 5 section rewrite planning must explicitly consume at least one simplify-first constraint
- **AND** simplify-first is not treated as must-avoid
