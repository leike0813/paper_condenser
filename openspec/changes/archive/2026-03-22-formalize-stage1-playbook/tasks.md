## 1. OpenSpec Artifacts

- [x] 1.1 Write `proposal.md` and define the new capability `stage1-playbook-clarification`
- [x] 1.2 Write `specs/stage1-playbook-clarification/spec.md` for Stage 1 substeps, question boundaries, field completion rules, and advancement gates
- [x] 1.3 Write `design.md` with the file-path-only and manuscript-profile-as-truth decisions

## 2. Main Skill Contract

- [x] 2.1 Update `paper-condenser/SKILL.md` to narrow the formal input contract to file-path input only
- [x] 2.2 Rewrite the Stage 1 recipe in `SKILL.md` with explicit substeps, mandatory script sequence, and completion gate
- [x] 2.3 Add Stage 1-specific question boundaries so Stage 1 does not pull Stage 2 decisions forward

## 3. Reference Documents

- [x] 3.1 Update `paper-condenser/references/stage-workflow.md` to expand Stage 1 into a concrete playbook
- [x] 3.2 Update `paper-condenser/references/artifact-protocol.md` to define Stage 1 minimum completion requirements for `manuscript-profile.json`
- [x] 3.3 Add `paper-condenser/references/stage1-playbook.md` for Stage 1 substeps, question triggers, failure handling, and the Stage 2 handoff checklist

## 4. Validation

- [x] 4.1 Run `openspec validate formalize-stage1-playbook`
- [x] 4.2 Run the external skill `quick_validate.py` check against `paper-condenser/`
- [x] 4.3 Manually verify that Stage 1 writes a usable understanding draft into `manuscript-profile.json` before Stage 2
