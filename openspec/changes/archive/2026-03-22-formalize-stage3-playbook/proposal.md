## Why

Stage 3 currently defines style analysis only at a high level. Another agent can see that it should update `style-profile.md`, but it still lacks a precise contract for analysis order, question boundaries, chapter-level completion rules, and the exact gate that must be satisfied before Stage 4 may begin.

## What Changes

- Define a stronger Stage 3 playbook with explicit style-analysis substeps, question triggers, and advancement gates.
- Clarify how the four existing `style-profile.md` sections behave as the authoritative Stage 3 output without introducing new status fields.
- Expand the Stage 3 execution contract and add a dedicated Stage 3 reference document.
- Keep the current `style-profile.md` template structure and all existing script interfaces unchanged.

## Capabilities

### New Capabilities

- `stage3-playbook-clarification`: Define the authoritative Stage 3 style-analysis playbook, including section-level writing expectations, question boundaries, and the gate for entering Stage 4.

### Modified Capabilities

None.

## Impact

Affected areas:
- `openspec/changes/formalize-stage3-playbook/`
- `paper-condenser/SKILL.md`
- `paper-condenser/references/stage-workflow.md`
- `paper-condenser/references/artifact-protocol.md`
- `paper-condenser/references/stage3-playbook.md`

No Python scripts, script interfaces, or template-structure changes are required.
