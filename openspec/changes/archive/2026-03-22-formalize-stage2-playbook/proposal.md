## Why

Stage 2 currently defines target setting only at a high level. Another agent can see which fields belong in `target-settings.json`, but it still lacks a precise contract for question order, draft-vs-confirmed handling, and the exact gate that must be satisfied before Stage 3 may begin.

## What Changes

- Define a stronger Stage 2 playbook with explicit target-setting substeps, readback confirmation, and advancement gates.
- Clarify how `target-settings.json` behaves as a draft while `user_confirmed=false` and as a locked setting source once the user explicitly confirms.
- Expand the Stage 2 execution contract and add a dedicated Stage 2 reference document.
- Keep the current `target-settings.json` schema and all existing script interfaces unchanged.

## Capabilities

### New Capabilities

- `stage2-playbook-clarification`: Define the authoritative Stage 2 target-setting playbook, including question sequencing, field update rules, readback confirmation, and the gate for entering Stage 3.

### Modified Capabilities

None.

## Impact

Affected areas:
- `openspec/changes/formalize-stage2-playbook/`
- `paper-condenser/SKILL.md`
- `paper-condenser/references/stage-workflow.md`
- `paper-condenser/references/artifact-protocol.md`
- `paper-condenser/references/stage2-playbook.md`

No Python scripts, script interfaces, or JSON schema changes are required.
