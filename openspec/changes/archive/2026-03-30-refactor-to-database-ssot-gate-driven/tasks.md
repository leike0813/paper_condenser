# Tasks

## 1. OpenSpec artifacts

- [x] 1.1 Create `proposal.md`
- [x] 1.2 Create `design.md`
- [x] 1.3 Create delta specs for the new runtime contract and modified stage capabilities
- [x] 1.4 Create `tasks.md`

## 2. Runtime implementation

- [x] 2.1 Add a shared runtime helper module for SQLite schema, gate evaluation, and rendering
- [x] 2.2 Add `paper-condenser/scripts/gate_runtime.py`
- [x] 2.3 Add `paper-condenser/scripts/stage_runtime.py`
- [x] 2.4 Retire the old file-first script surface into wrappers or deprecated shims

## 3. Skill contract rewrite

- [x] 3.1 Rewrite `paper-condenser/SKILL.md` to declare SQLite SSOT and gate-driven execution
- [x] 3.2 Rewrite `paper-condenser/references/artifact-protocol.md`
- [x] 3.3 Rewrite `paper-condenser/references/stage-workflow.md`
- [x] 3.4 Rewrite stage playbooks for Stage 1-5
- [x] 3.5 Rewrite `paper-condenser/references/supporting-elements-playbook.md`
- [x] 3.6 Rewrite `paper-condenser/references/rewrite-report-playbook.md`
- [x] 3.7 Add `paper-condenser/references/runtime-database-contract.md`
- [x] 3.8 Add `paper-condenser/references/gate-and-stage-runtime.md`
- [x] 3.9 Update `README.md`

## 4. Validation

- [x] 4.1 Run `openspec validate refactor-to-database-ssot-gate-driven`
- [x] 4.2 Run `quick_validate.py paper-condenser`
- [x] 4.3 Run `mypy` on the new runtime scripts
- [x] 4.4 Run a smoke flow covering bootstrap, gate progression, stage persistence, and rendered final outputs
