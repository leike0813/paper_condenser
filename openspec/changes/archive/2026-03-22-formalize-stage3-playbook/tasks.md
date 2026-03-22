## 1. OpenSpec Artifacts

- [x] 1.1 Write `proposal.md` and define the new capability `stage3-playbook-clarification`
- [x] 1.2 Write `specs/stage3-playbook-clarification/spec.md` for Stage 3 substeps, question boundaries, section completion rules, and advancement gate
- [x] 1.3 Write `design.md` with the existing-template and content-completeness decisions

## 2. Main Skill Contract

- [x] 2.1 Update `paper-condenser/SKILL.md` to rewrite Stage 3 as an ordered style-analysis playbook
- [x] 2.2 Add Stage 3-specific question boundaries so Stage 3 does not pull Stage 4 concerns forward
- [x] 2.3 Make the Stage 4 precondition depend on a usable `style-profile.md`

## 3. Reference Documents

- [x] 3.1 Update `paper-condenser/references/stage-workflow.md` to expand Stage 3 into a concrete playbook
- [x] 3.2 Update `paper-condenser/references/artifact-protocol.md` to define completion behavior for `style-profile.md`
- [x] 3.3 Add `paper-condenser/references/stage3-playbook.md` for Stage 3 analysis order, failure handling, and the Stage 4 handoff checklist

## 4. Validation

- [x] 4.1 Run `openspec validate formalize-stage3-playbook`
- [x] 4.2 Run the external skill `quick_validate.py` check against `paper-condenser/`
- [x] 4.3 Manually verify that Stage 3 persists style analysis into all required sections and does not pull Stage 4 planning forward
