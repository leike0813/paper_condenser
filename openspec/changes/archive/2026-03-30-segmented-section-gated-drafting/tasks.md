# Tasks

## 1. OpenSpec artifacts

- [x] 1.1 Create `proposal.md`
- [x] 1.2 Create `design.md`
- [x] 1.3 Create delta specs for segmented section drafting and gate/runtime updates
- [x] 1.4 Create `tasks.md`

## 2. Runtime schema and gate

- [x] 2.1 Extend runtime schema for scope segments, section rewrite plans, section drafts, draft provenance, draft events, and output targets
- [x] 2.2 Add new gated actions for segmentation, section planning, section drafting, approval, output target persistence, and final bundle rendering
- [x] 2.3 Update gate logic and workflow-state fields for section-loop drafting

## 3. Rendering and outputs

- [x] 3.1 Add render templates for scope segments, section rewrite plans, section drafting board, and section review artifacts
- [x] 3.2 Update runtime rendering to emit the new views and section review files
- [x] 3.3 Render final outputs only after all sections are approved and output target is confirmed
- [x] 3.4 Copy used images into the final output directory and rewrite image paths

## 4. Skill contract rewrite

- [x] 4.1 Update `paper-condenser/SKILL.md`
- [x] 4.2 Update `paper-condenser/references/runtime-database-contract.md`
- [x] 4.3 Update `paper-condenser/references/artifact-protocol.md`
- [x] 4.4 Update `paper-condenser/references/stage-workflow.md`
- [x] 4.5 Update stage playbooks for scope segmentation and section-loop drafting
- [x] 4.6 Add a section drafting appendix

## 5. Validation

- [x] 5.1 Run `openspec validate segmented-section-gated-drafting`
- [x] 5.2 Run `quick_validate.py paper-condenser`
- [x] 5.3 Run `mypy` on the runtime stack
- [x] 5.4 Run a smoke flow covering segmentation, section drafting, approval, output target, and final bundle rendering
