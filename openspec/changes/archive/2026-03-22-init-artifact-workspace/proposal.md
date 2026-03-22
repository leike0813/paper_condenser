## Why

The package now ships formal artifact templates, but initializing a working artifact directory still depends on manual file copying. That leaves a deterministic, repetitive workflow step outside the package contract and increases the chance of drift or missing files.

## What Changes

- Add a formal artifact-initialization script at `paper-condenser/scripts/init_artifacts.py`.
- Define a stable CLI contract based on `--artifact-root`.
- Initialize runtime artifact directories by copying package templates into the target directory.
- Preserve existing files by filling only missing artifacts.
- Update the skill instructions so this script becomes the official initialization entrypoint.

## Capabilities

### New Capabilities

- `artifact-workspace-init`: Initialize a task-local artifact workspace from package-owned templates through a deterministic script interface.

### Modified Capabilities

None.

## Impact

Affected areas:
- `openspec/changes/init-artifact-workspace/`
- `paper-condenser/scripts/`
- `paper-condenser/SKILL.md`

No changes to the four-artifact protocol, OpenAI metadata, or user-facing runtime decisions.
