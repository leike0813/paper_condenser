# Tasks

## 1. OpenSpec artifacts

- [x] 1.1 Create `proposal.md`
- [x] 1.2 Create `design.md`
- [x] 1.3 Create delta specs for the raw/semantic dual-layer source model
- [x] 1.4 Create `tasks.md`

## 2. Runtime schema and gate

- [x] 2.1 Add `raw_scope_segments`, `semantic_source_units`, `semantic_source_unit_members`, and `semantic_source_unit_elements`
- [x] 2.2 Replace the Stage 2 gate path with `persist_manuscript_analysis` -> `persist_raw_scope_segments` -> `persist_semantic_source_units`
- [x] 2.3 Deprecate `persist_scope_segments`

## 3. Downstream source binding

- [x] 3.1 Update section rewrite plans to bind primarily to semantic units
- [x] 3.2 Update section draft provenance to bind to semantic units only
- [x] 3.3 Add validation that referenced semantic units actually exist

## 4. Rendered views and templates

- [x] 4.1 Keep `07-scope-segments.md` as a raw-layer view
- [x] 4.2 Add `08-semantic-source-units.md`
- [x] 4.3 Renumber section rewrite plan and section drafting board views/templates
- [x] 4.4 Update section review rendering to expose semantic-unit provenance

## 5. Documentation

- [x] 5.1 Update `paper-condenser/SKILL.md`
- [x] 5.2 Update `artifact-protocol.md`
- [x] 5.3 Update `runtime-database-contract.md`
- [x] 5.4 Update `stage-workflow.md`
- [x] 5.5 Update `stage2-playbook.md`, `stage5-playbook.md`, `stage6-playbook.md`
- [x] 5.6 Update `supporting-elements-playbook.md`, `rewrite-report-playbook.md`, `README.md`

## 6. Validation

- [x] 6.1 Run `openspec validate refactor-scope-segmentation-to-raw-semantic`
- [x] 6.2 Run `quick_validate.py paper-condenser`
- [x] 6.3 Run `mypy` on the runtime stack
- [x] 6.4 Run a smoke flow covering raw segmentation, semantic units, section planning, and section provenance
