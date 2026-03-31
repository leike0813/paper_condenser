# Tasks

## 1. Runtime gate reshaping

- [x] Merge `persist_style_profile` into Stage 3 gate order
- [x] Renumber workflow stages after Stage 3
- [x] Update instruction refs and pending-confirmation stage ownership

## 2. Stage playbook alignment

- [x] Expand `stage3-playbook.md` to include the style-profile substep
- [x] Turn `stage4-playbook.md` into the condensation-plan playbook
- [x] Turn `stage5-playbook.md` into the final-drafting playbook
- [x] Remove `stage6-playbook.md` from the active reference set

## 3. Skill and reference updates

- [x] Update `SKILL.md` stage overview, state machine, and reference index
- [x] Update `stage-workflow.md`, `gate-and-stage-runtime.md`, and `runtime-database-contract.md`
- [x] Update `artifact-protocol.md`, `supporting-elements-playbook.md`, `rewrite-report-playbook.md`, and `README.md`
- [x] Update main specs text that still refers to the old stage numbering

## 4. Validation

- [x] Run `openspec validate merge-style-profile-into-stage3`
- [x] Run `quick_validate.py paper-condenser`
- [x] Run `mypy` on runtime scripts
