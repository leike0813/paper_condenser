## ADDED Requirements

### Requirement: Gate returns a minimal payload example for the next action

The gate runtime MUST return a machine-readable minimal payload example together with `next_action`.

#### Scenario: The next action requires payload

- **WHEN** `gate_runtime.py` returns a payload-bearing `next_action`
- **THEN** the result includes `next_action_payload_example`
- **AND** that field contains a minimal JSON object that can be used as the starting shape for the next stage write

#### Scenario: The next action does not require payload

- **WHEN** `gate_runtime.py` returns a no-payload `next_action`
- **THEN** `next_action_payload_example` is `null`
