## Why

The package already contains several formal scripts and a staged workflow, but it still does not define a strict execution contract for how scripts and the LLM should collaborate. Another agent can see the available entrypoints, yet it still lacks an authoritative answer to which tasks must be delegated to scripts, which tasks must remain with the LLM, and which gates prevent progression to later stages.

## What Changes

- Define a strong execution contract for script responsibilities, LLM responsibilities, and forbidden delegation.
- Rewrite the middle section of `paper-condenser/SKILL.md` from descriptive guidance into a staged execution contract.
- Refactor `references/stage-workflow.md` to mirror the contract as per-stage recipes with gates.
- Keep existing script interfaces stable while clarifying when each one is mandatory.
- Permit only minor wording-level alignment with current script behavior, without refactoring the scripts themselves.

## Capabilities

### New Capabilities

- `execution-contract-clarification`: Establish a strong execution contract for how scripts and the LLM collaborate across each stage of the paper condensation workflow.

### Modified Capabilities

None.

## Impact

Affected areas:
- `openspec/changes/formalize-execution-contract/`
- `paper-condenser/SKILL.md`
- `paper-condenser/references/stage-workflow.md`

No changes to the artifact model or script interfaces are required.
