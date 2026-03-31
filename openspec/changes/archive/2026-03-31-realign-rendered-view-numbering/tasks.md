## 1. Runtime And Template Mapping

- [x] 1.1 Update `runtime_core.py` to use workflow-aligned rendered view filenames
- [x] 1.2 Update `runtime_rendering.py` template mapping to the new numbering
- [x] 1.3 Rename the Jinja2 template files to match the new workflow-aligned numbering

## 2. Skill And Reference Docs

- [x] 2.1 Update `SKILL.md` rendered-view inventory and references
- [x] 2.2 Update `artifact-protocol.md` template mapping and rendered-view sections
- [x] 2.3 Update stage playbooks and supporting docs that reference numbered runtime views

## 3. Validation

- [x] 3.1 Run `openspec validate realign-rendered-view-numbering`
- [x] 3.2 Run `quick_validate.py paper-condenser`
- [x] 3.3 Run `mypy` on the runtime rendering stack
