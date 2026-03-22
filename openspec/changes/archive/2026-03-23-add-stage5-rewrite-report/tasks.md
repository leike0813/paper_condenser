## 1. OpenSpec Artifacts

- [x] 1.1 Write `proposal.md` and define `rewrite-report-output-clarification`
- [x] 1.2 Write the new capability spec for persisted rewrite-report output and mixed-granularity traceability
- [x] 1.3 Write modified capability specs for `stage5-playbook-clarification` and `supporting-elements-flow-clarification`
- [x] 1.4 Write `design.md` with the “Markdown-only companion output + no new script” decisions

## 2. Skill Contract

- [x] 2.1 Update `paper-condenser/SKILL.md` so Stage 5 produces both `final-draft.tex` and `rewrite-report.md`
- [x] 2.2 Update the Stage 5 gate so report generation is mandatory before completion
- [x] 2.3 Add the new report playbook to the resource list

## 3. Reference Documents

- [x] 3.1 Update `paper-condenser/references/stage5-playbook.md` with a dedicated rewrite-report generation step
- [x] 3.2 Update `paper-condenser/references/stage-workflow.md` to reflect the new Stage 5 substep order and gate
- [x] 3.3 Update `paper-condenser/references/artifact-protocol.md` to define `rewrite-report.md`
- [x] 3.4 Add `paper-condenser/references/rewrite-report-playbook.md`
- [x] 3.5 Update `paper-condenser/references/supporting-elements-playbook.md` so key supporting elements must be reflected in the report

## 4. Repository Docs

- [x] 4.1 Update `README.md` to mention rewrite-report generation as part of current Stage 5 capability

## 5. Validation

- [x] 5.1 Run `openspec validate add-stage5-rewrite-report`
- [x] 5.2 Run `quick_validate.py paper-condenser`
- [x] 5.3 Verify by inspection that Stage 5 completion now requires both `final-draft.tex` and `rewrite-report.md`
