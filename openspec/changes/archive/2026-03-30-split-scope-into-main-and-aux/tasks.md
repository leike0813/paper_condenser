# Tasks

## 1. OpenSpec artifacts

- [x] 1.1 Create `proposal.md`
- [x] 1.2 Create `design.md`
- [x] 1.3 Create delta spec for the main/aux scope model
- [x] 1.4 Create `tasks.md`

## 2. Runtime changes

- [x] 2.1 Replace Stage 2 analysis payload from single-scope fields to `main_scope + main_scope_locator + aux_scopes[*]`
- [x] 2.2 Extend `raw_scope_segments` with `scope_role`, `scope_bucket_id`, and `scope_label`
- [x] 2.3 Update raw segmentation to extract from main first, then aux buckets, and persist into one globally ordered table
- [x] 2.4 Preserve main/aux composition when expanding semantic provenance
- [x] 2.5 Require section plans to explain aux-backed semantic sources

## 3. Rendered views and templates

- [x] 3.1 Update manuscript profile rendering to show main and aux scopes
- [x] 3.2 Update raw scope segment view to show role and bucket metadata
- [x] 3.3 Update semantic-unit, section-plan, and section-review rendering to expose main/aux member composition
- [x] 3.4 Update rewrite-report rendering to expose aux-backed provenance where applicable

## 4. Documentation

- [x] 4.1 Update `paper-condenser/SKILL.md`
- [x] 4.2 Update `runtime-database-contract.md`
- [x] 4.3 Update `artifact-protocol.md`
- [x] 4.4 Update `stage-workflow.md`
- [x] 4.5 Update `stage2-playbook.md`, `stage5-playbook.md`, `stage6-playbook.md`
- [x] 4.6 Update `supporting-elements-playbook.md`, `rewrite-report-playbook.md`, `gate-and-stage-runtime.md`, and `README.md`

## 5. Validation

- [x] 5.1 Run `openspec validate split-scope-into-main-and-aux`
- [x] 5.2 Run `quick_validate.py paper-condenser`
- [x] 5.3 Run `mypy` on the runtime stack
- [x] 5.4 Run a smoke flow covering main-only and main+aux provenance
