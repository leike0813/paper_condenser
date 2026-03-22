## 1. OpenSpec Artifacts

- [x] 1.1 Write `proposal.md` and define the new capability `stage5-playbook-clarification`
- [x] 1.2 Write `specs/stage5-playbook-clarification/spec.md` for Stage 5 substeps, final-output persistence, and fallback rules
- [x] 1.3 Write modified capability specs for `stage1-intake-bootstrap`, `stage2-playbook-clarification`, and `stage1-playbook-clarification`
- [x] 1.4 Write `design.md` with the single-file-LaTeX, built-in-template, and minimal-script-change decisions

## 2. Main Skill Contract

- [x] 2.1 Update `paper-condenser/SKILL.md` to narrow formal input to a single `.tex` file path
- [x] 2.2 Update Stage 2 to include `latex_template_id` in the confirmed target-setting bundle
- [x] 2.3 Rewrite Stage 5 as an ordered LaTeX drafting playbook and define `final-draft.tex` as the persisted output truth

## 3. Reference Documents And Assets

- [x] 3.1 Update `paper-condenser/references/stage-workflow.md` to expand Stage 5 into a concrete LaTeX drafting playbook
- [x] 3.2 Update `paper-condenser/references/artifact-protocol.md` to document `latex_template_id` and `final-draft.tex`
- [x] 3.3 Update `paper-condenser/references/stage2-playbook.md` so template selection is part of Stage 2 collection and confirmation
- [x] 3.4 Add `paper-condenser/references/stage5-playbook.md`
- [x] 3.5 Add built-in single-file LaTeX preset templates under `paper-condenser/assets/latex-templates/`
- [x] 3.6 Update `paper-condenser/assets/artifact-templates/target-settings.json` to include `latex_template_id`

## 4. Script Changes

- [x] 4.1 Update `paper-condenser/scripts/stage1_intake.py` to support `single_file:tex`
- [x] 4.2 Keep deterministic intake behavior unchanged apart from source-type support
- [x] 4.3 Add `paper-condenser/scripts/init_final_draft.py` for Stage 5 preflight and final-draft skeleton initialization

## 5. Validation

- [x] 5.1 Run `openspec validate formalize-stage5-latex-drafting`
- [x] 5.2 Run the external skill `quick_validate.py` check against `paper-condenser/`
- [x] 5.3 Run `mypy` on `paper-condenser/scripts/stage1_intake.py`
- [x] 5.4 Verify `.tex` bootstrap + intake succeeds and writes deterministic intake fields
- [x] 5.5 Verify `init_final_draft.py` succeeds only when target settings are confirmed and the condensation plan is approved
