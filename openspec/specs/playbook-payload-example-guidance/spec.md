# playbook-payload-example-guidance Specification

## Purpose
TBD - created by archiving change compress-skill-md-and-surface-payload-examples. Update Purpose after archive.
## Requirements
### Requirement: Stage playbooks show minimal payload examples

Payload-bearing stage playbooks MUST provide minimal JSON examples instead of only field-name lists.

#### Scenario: Agent needs payload details for a stage write

- **WHEN** the Agent opens the relevant `stageN-playbook.md`
- **THEN** it finds a `Minimal Payload Example`
- **AND** it finds short notes explaining any important constraints or optional fields

#### Scenario: A stage action does not accept payload

- **WHEN** the Agent opens the relevant playbook section for a script-only action
- **THEN** the playbook states that no payload is needed and the action only requires `--artifact-root`

