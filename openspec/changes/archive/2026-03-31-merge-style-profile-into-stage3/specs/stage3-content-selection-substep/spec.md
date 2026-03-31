## MODIFIED Requirements

### Requirement: Stage 3 includes a dedicated content-selection substep

The runtime MUST treat Stage 3 target setting, content-selection confirmation, style profiling, and final confirmation as separate gated actions inside the same stage.

#### Scenario: Stage 3 content selection is confirmed

- **WHEN** Stage 3 basics are persisted
- **AND** content selection is confirmed
- **THEN** gate returns `persist_style_profile`
- **AND** the runtime does not allow Stage 4 until style profiling is complete
- **AND** `finalize_target_settings` remains the final Stage 3 confirmation step
