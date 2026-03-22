## 1. OpenSpec Artifacts

- [x] 1.1 Write `proposal.md` and define the new capability `stage4-playbook-clarification`
- [x] 1.2 Write `specs/stage4-playbook-clarification/spec.md` for Stage 4 substeps, question boundaries, section completion rules, and approval gate
- [x] 1.3 Write `design.md` with the existing-template and approval-line decisions

## 2. Main Skill Contract

- [x] 2.1 Update `paper-condenser/SKILL.md` to rewrite Stage 4 as an ordered condensation-planning playbook
- [x] 2.2 Add Stage 4-specific question boundaries so Stage 4 does not pull Stage 5 drafting forward
- [x] 2.3 Make the Stage 5 precondition depend on an approved `condensation-plan.md`

## 3. Reference Documents

- [x] 3.1 Update `paper-condenser/references/stage-workflow.md` to expand Stage 4 into a concrete playbook
- [x] 3.2 Update `paper-condenser/references/artifact-protocol.md` to define completion behavior for `condensation-plan.md`
- [x] 3.3 Add `paper-condenser/references/stage4-playbook.md` for Stage 4 planning order, failure handling, and the Stage 5 handoff checklist

## 4. Validation

- [x] 4.1 Run `openspec validate formalize-stage4-playbook`
- [x] 4.2 Run the external skill `quick_validate.py` check against `paper-condenser/`
- [x] 4.3 Manually verify that Stage 4 persists all planning sections and only enters Stage 5 after `Status: approved`
