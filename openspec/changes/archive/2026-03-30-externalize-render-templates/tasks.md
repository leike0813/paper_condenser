# Tasks

## 1. OpenSpec artifacts

- [x] 1.1 Create `proposal.md`
- [x] 1.2 Create `design.md`
- [x] 1.3 Create delta specs for the render-template layer and runtime rendering requirements
- [x] 1.4 Create `tasks.md`

## 2. Template assets

- [x] 2.1 Add `paper-condenser/assets/render-templates/`
- [x] 2.2 Add six Jinja2 templates for the read-only Markdown views

## 3. Runtime refactor

- [x] 3.1 Add `paper-condenser/scripts/runtime_rendering.py`
- [x] 3.2 Refactor `paper-condenser/scripts/runtime_core.py` to build view-models and delegate rendering
- [x] 3.3 Keep gate/stage CLI behavior unchanged

## 4. Documentation

- [x] 4.1 Update `paper-condenser/SKILL.md`
- [x] 4.2 Update `paper-condenser/references/artifact-protocol.md`
- [x] 4.3 Update `paper-condenser/references/runtime-database-contract.md`
- [x] 4.4 Update `README.md`

## 5. Validation

- [x] 5.1 Run `openspec validate externalize-render-templates`
- [x] 5.2 Run `quick_validate.py paper-condenser`
- [x] 5.3 Run `mypy` on the runtime render stack
- [x] 5.4 Run a smoke flow that re-renders the six Markdown views through external templates
