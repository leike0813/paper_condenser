# Tasks

## 1. Runtime gate and persistence

- [x] Add `confirm_condensation_plan` and `confirm_section_rewrite_plan` actions
- [x] Update Stage 5 gate order to require both approvals before Stage 6
- [x] Enrich section rewrite plan persistence with summary / strategy / figure-table / reference fields
- [x] Enforce assembly-only checks in final bundle rendering

## 2. Rendered views and templates

- [x] Update `05-condensation-plan.md.j2`
- [x] Update `09-section-rewrite-plan.md.j2`
- [x] Update `10-section-drafting-board.md.j2`
- [x] Update `section-review.md.j2`

## 3. Skill/docs

- [x] Update `SKILL.md`
- [x] Update `stage5-playbook.md`
- [x] Update `stage6-playbook.md`
- [x] Update `stage-workflow.md`
- [x] Update `runtime-database-contract.md`
- [x] Update `artifact-protocol.md`
- [x] Update `supporting-elements-playbook.md`

## 4. Validation

- [x] Run `openspec validate tighten-stage5-approvals-and-assembly-boundary`
- [x] Run `quick_validate.py paper-condenser`
- [x] Run `mypy` on runtime scripts
