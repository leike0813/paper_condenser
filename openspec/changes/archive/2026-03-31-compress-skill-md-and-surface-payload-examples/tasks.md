# Tasks

## 1. Gate payload examples

- [x] Add `next_action_payload_example` to gate output
- [x] Provide minimal JSON examples for all payload-bearing actions
- [x] Return `null` for no-payload actions

## 2. Skill/docs refactor

- [x] Compress `SKILL.md` to remove payload field inventories from `Action Summary`
- [x] Keep stage purpose / flow explanation intact in `SKILL.md`
- [x] Update `gate-and-stage-runtime.md` to document `next_action_payload_example`
- [x] Update `stage-workflow.md` to point payload lookup to gate / playbooks

## 3. Playbook payload examples

- [x] Update `stage2-playbook.md` with minimal payload examples
- [x] Update `stage3-playbook.md` with minimal payload examples
- [x] Update `stage4-playbook.md` with minimal payload examples
- [x] Update `stage5-playbook.md` with minimal payload examples
- [x] Update `stage6-playbook.md` with minimal payload examples

## 4. Validation

- [x] Verify `paper-condenser/SKILL.md` is under 500 lines
- [x] Run `openspec validate compress-skill-md-and-surface-payload-examples`
- [x] Run `quick_validate.py paper-condenser`
- [x] Run `mypy` on `runtime_core.py` and `gate_runtime.py`
