## 1. OpenSpec Artifacts

- [x] 1.1 Write `proposal.md` and define `supporting-elements-flow-clarification`
- [x] 1.2 Write the new capability spec for supporting-elements inventory, planning, and migration
- [x] 1.3 Write modified capability specs for Stage 1 through Stage 5 playbooks
- [x] 1.4 Write `design.md` with the “reuse four truth sources + Stage 1 helper script” decisions

## 2. Runtime Truth Sources

- [x] 2.1 Extend `paper-condenser/assets/artifact-templates/manuscript-profile.json` with supporting-elements inventory fields
- [x] 2.2 Extend `paper-condenser/assets/artifact-templates/target-settings.json` with figure/table and reference preferences
- [x] 2.3 Extend `paper-condenser/assets/artifact-templates/condensation-plan.md` with figure/table and reference planning sections

## 3. Skill Contract And Playbooks

- [x] 3.1 Update `paper-condenser/SKILL.md` to add the supporting-elements flow across Stage 1, Stage 2, Stage 3, Stage 4, and Stage 5
- [x] 3.2 Update `paper-condenser/references/artifact-protocol.md` to document the new fields and section responsibilities
- [x] 3.3 Update `paper-condenser/references/stage-workflow.md` to add supporting-elements script calls and gates
- [x] 3.4 Update Stage 1 through Stage 5 playbooks to reflect the new handling rules
- [x] 3.5 Add `paper-condenser/references/supporting-elements-playbook.md`

## 4. Script Changes

- [x] 4.1 Add `paper-condenser/scripts/extract_supporting_elements.py`
- [x] 4.2 Keep the new script deterministic and `.tex`-only
- [x] 4.3 Leave semantic keep/drop decisions to the LLM

## 5. Validation

- [x] 5.1 Run `openspec validate formalize-figures-tables-references-flow`
- [x] 5.2 Run `quick_validate.py paper-condenser`
- [x] 5.3 Run `mypy` on the new helper script and touched Python files
- [x] 5.4 Verify supporting-elements extraction succeeds on a `.tex` input with figures, tables, citations, and bibliography structure
