## 1. OpenSpec Artifacts

- [x] 1.1 Write `proposal.md` and define the new capability `interactive-condensation-workflow`
- [x] 1.2 Write `specs/interactive-condensation-workflow/spec.md` for staged execution, artifact rules, user-owned decisions, and drafting gates
- [x] 1.3 Write `design.md` with the task-local artifact directory, four-file state model, and Chinese-first documentation decision

## 2. Executable Skill Protocol

- [x] 2.1 Rewrite `paper-condenser/SKILL.md` into an executable workflow with explicit input contract, stage flow, artifact protocol, question policy, and drafting gate
- [x] 2.2 Keep the public invocation name and existing `agents/openai.yaml` interface metadata unchanged
- [x] 2.3 Define the artifact root as `artifacts/<document-slug>/` and use the agreed four-file artifact set

## 3. Package References

- [x] 3.1 Add `paper-condenser/references/stage-workflow.md` with per-stage goals, required questions, inputs, outputs, and gates
- [x] 3.2 Add `paper-condenser/references/artifact-protocol.md` with artifact purposes, minimal fields, and update timing

## 4. Validation

- [x] 4.1 Run `openspec validate author-executable-skill-workflow`
- [x] 4.2 Run the external skill `quick_validate.py` check against `paper-condenser/`
- [x] 4.3 Verify that final drafting is explicitly gated on artifact completeness and user approval
