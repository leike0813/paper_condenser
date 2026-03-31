## MODIFIED Requirements

### Requirement: Runtime progression is gate-driven

The package MUST use a single gate entry to determine the only allowed next action.

#### Scenario: A runtime workspace is resumed

- **WHEN** `gate_runtime.py` is run against an existing `artifact-root`
- **THEN** it returns `workflow_stage`
- **AND** it returns `next_action`
- **AND** it returns blockers and pending confirmations when progression is not allowed
- **AND** it returns `runtime_digest` as a stable runtime-discipline summary

#### Scenario: A bootstrap gate is inspected

- **WHEN** `gate_runtime.py` is run with `--source-path` before workspace initialization
- **THEN** it still returns `runtime_digest`
- **AND** the digest content matches the digest returned by resume-time gate calls
