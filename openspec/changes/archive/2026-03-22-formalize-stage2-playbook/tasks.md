## 1. OpenSpec Artifacts

- [x] 1.1 Write `proposal.md` and define the new capability `stage2-playbook-clarification`
- [x] 1.2 Write `specs/stage2-playbook-clarification/spec.md` for Stage 2 substeps, question boundaries, field update rules, and confirmation gate
- [x] 1.3 Write `design.md` with the existing-schema and draft-via-partial-fill decisions

## 2. Main Skill Contract

- [x] 2.1 Update `paper-condenser/SKILL.md` to rewrite Stage 2 as an ordered target-setting playbook
- [x] 2.2 Add Stage 2-specific question boundaries so Stage 2 does not pull Stage 3 or Stage 4 concerns forward
- [x] 2.3 Make the Stage 3 precondition depend on confirmed `target-settings.json`

## 3. Reference Documents

- [x] 3.1 Update `paper-condenser/references/stage-workflow.md` to expand Stage 2 into a concrete playbook
- [x] 3.2 Update `paper-condenser/references/artifact-protocol.md` to define draft-vs-confirmed behavior for `target-settings.json`
- [x] 3.3 Add `paper-condenser/references/stage2-playbook.md` for Stage 2 question order, failure handling, and the Stage 3 handoff checklist

## 4. Validation

- [x] 4.1 Run `openspec validate formalize-stage2-playbook`
- [x] 4.2 Run the external skill `quick_validate.py` check against `paper-condenser/`
- [x] 4.3 Manually verify that Stage 2 persists partial settings, performs readback, and only sets `user_confirmed=true` after explicit confirmation
