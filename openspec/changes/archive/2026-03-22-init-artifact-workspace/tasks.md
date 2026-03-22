## 1. OpenSpec Artifacts

- [x] 1.1 Write `proposal.md` and define the new capability `artifact-workspace-init`
- [x] 1.2 Write `specs/artifact-workspace-init/spec.md` for script entrypoint, CLI contract, template copying, non-overwrite behavior, and JSON output
- [x] 1.3 Write `design.md` with the narrow CLI and deterministic initialization decisions

## 2. Script Implementation

- [x] 2.1 Add `paper-condenser/scripts/init_artifacts.py`
- [x] 2.2 Implement `--artifact-root` handling, template discovery, directory creation, and copy-missing-only behavior
- [x] 2.3 Return JSON with `artifact_root`, `created_files`, and `skipped_files`

## 3. Skill Integration

- [x] 3.1 Update `paper-condenser/SKILL.md` to make `scripts/init_artifacts.py` the formal initialization entrypoint
- [x] 3.2 State that artifact initialization must happen before stage workflow continues when the task directory is absent

## 4. Validation

- [x] 4.1 Run `openspec validate init-artifact-workspace`
- [x] 4.2 Run the script against a fresh `/tmp` artifact directory and verify it creates four files
- [x] 4.3 Run the script again against the same directory and verify it skips existing files without overwriting
- [x] 4.4 Run the external skill `quick_validate.py` check against `paper-condenser/`
- [x] 4.5 Run `mypy paper-condenser/scripts/init_artifacts.py`
