## 1. OpenSpec Artifacts

- [x] 1.1 Write `proposal.md` and define the new capability `execution-contract-clarification`
- [x] 1.2 Write `specs/execution-contract-clarification/spec.md` for script/LLM responsibilities, forbidden delegation, mandatory entry sequences, and stage gates
- [x] 1.3 Write `design.md` with the strong-contract and stage-recipe decisions

## 2. Execution Contract

- [x] 2.1 Rewrite `paper-condenser/SKILL.md` to add `Script Responsibilities`, `LLM Responsibilities`, and `Forbidden Delegation`
- [x] 2.2 Rewrite the stage section into per-stage recipes with preconditions, required script calls, LLM tasks, outputs, and do-not-advance gates
- [x] 2.3 Keep existing script interfaces unchanged while clarifying when each one is mandatory

## 3. Detailed Workflow Reference

- [x] 3.1 Update `paper-condenser/references/stage-workflow.md` to mirror the stage-recipe structure
- [x] 3.2 Keep the reference aligned with the main contract without repeating every hard rule verbatim

## 4. Validation

- [x] 4.1 Run `openspec validate formalize-execution-contract`
- [x] 4.2 Run the external skill `quick_validate.py` check against `paper-condenser/`
- [x] 4.3 Manually verify that script-only work, LLM-only work, forbidden delegation, and stage gates are all explicit
