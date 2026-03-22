## Why

Stage 4 currently defines condensation planning only at a high level. Another agent can see that it should update `condensation-plan.md`, but it still lacks a precise contract for planning order, question boundaries, section-level completion rules, and the exact approval gate that must be satisfied before final drafting may begin.

## What Changes

- Define a stronger Stage 4 playbook with explicit planning substeps, question triggers, and approval gates.
- Clarify how the six existing `condensation-plan.md` sections behave as the authoritative Stage 4 output without introducing new status fields.
- Expand the Stage 4 execution contract and add a dedicated Stage 4 reference document.
- Keep the current `condensation-plan.md` template structure and all existing script interfaces unchanged.

## Capabilities

### New Capabilities

- `stage4-playbook-clarification`: Define the authoritative Stage 4 condensation-planning playbook, including section-level writing expectations, approval handling, and the gate for entering Stage 5.

### Modified Capabilities

None.

## Impact

Affected areas:
- `openspec/changes/formalize-stage4-playbook/`
- `paper-condenser/SKILL.md`
- `paper-condenser/references/stage-workflow.md`
- `paper-condenser/references/artifact-protocol.md`
- `paper-condenser/references/stage4-playbook.md`

No Python scripts, script interfaces, or template-structure changes are required.
