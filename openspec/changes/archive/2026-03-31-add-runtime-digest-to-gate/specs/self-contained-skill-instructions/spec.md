## MODIFIED Requirements

### Requirement: References Must Be Explicitly On-Demand

`paper-condenser/SKILL.md` MUST explicitly state that `references/` documents are supplementary and should be loaded on demand.

#### Scenario: Agent resumes after a long context

- **WHEN** the Agent resumes execution from a gate result
- **THEN** it is instructed to read the gate-provided `runtime_digest` first
- **AND** then to inspect `next_action` and `next_action_payload_example`
- **AND** only then to load stage references on demand if needed
