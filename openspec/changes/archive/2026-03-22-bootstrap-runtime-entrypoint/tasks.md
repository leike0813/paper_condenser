## 1. OpenSpec Artifacts

- [x] 1.1 Write `proposal.md` and define the new capability `runtime-entrypoint-bootstrap`
- [x] 1.2 Write `specs/runtime-entrypoint-bootstrap/spec.md` for source-path input, slug derivation, reuse of initialization logic, and metadata seeding
- [x] 1.3 Write `design.md` with file-path-only scope and fail-fast collision behavior

## 2. Runtime Bootstrap Script

- [x] 2.1 Add `paper-condenser/scripts/bootstrap_runtime.py`
- [x] 2.2 Implement `--source-path` validation, slug normalization, and `artifacts/<document-slug>/` selection
- [x] 2.3 Reuse `init_artifacts.py` to initialize the workspace and seed `manuscript-profile.json` with deterministic metadata
- [x] 2.4 Return JSON with `document_slug`, `artifact_root`, and `created_files`

## 3. Skill Integration

- [x] 3.1 Update `paper-condenser/SKILL.md` so file-path input flows start with `bootstrap_runtime.py`
- [x] 3.2 Keep `init_artifacts.py` documented as the lower-level initialization layer

## 4. Validation

- [x] 4.1 Run `openspec validate bootstrap-runtime-entrypoint`
- [x] 4.2 Run the runtime bootstrap against a real file path and verify it creates `artifacts/<document-slug>/` and seeds metadata
- [x] 4.3 Run the bootstrap a second time against the same file and verify it fails because the artifact root already exists
- [x] 4.4 Run the external skill `quick_validate.py` check against `paper-condenser/`
- [x] 4.5 Run `mypy paper-condenser/scripts/bootstrap_runtime.py paper-condenser/scripts/init_artifacts.py`
