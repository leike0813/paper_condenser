## Why

Stage 1 currently defines only a high-level recipe for manuscript understanding. Another agent can see that it must run the existing bootstrap and intake scripts, but it still lacks a precise operational contract for Stage 1 substeps, manuscript-profile field completion, and the boundary between Stage 1 questions and later-stage decisions.

## What Changes

- Narrow the skill's formal input contract to file-path input only for the first supported version.
- Define a stronger Stage 1 playbook with explicit substeps, field-write expectations, question triggers, and completion gates.
- Clarify `manuscript-profile.json` as the Stage 1 source of truth and define the minimum usable draft required before Stage 2 can begin.
- Add a dedicated Stage 1 reference document so the main skill contract stays authoritative without becoming overloaded.

## Capabilities

### New Capabilities

- `stage1-playbook-clarification`: Define the authoritative Stage 1 manuscript-understanding playbook, including required script sequence, LLM-only analysis steps, field completion rules, and advancement gates.

### Modified Capabilities

None.

## Impact

Affected areas:
- `openspec/changes/formalize-stage1-playbook/`
- `paper-condenser/SKILL.md`
- `paper-condenser/references/stage-workflow.md`
- `paper-condenser/references/artifact-protocol.md`
- `paper-condenser/references/stage1-playbook.md`

No Python scripts or script interfaces are changed in this proposal.
