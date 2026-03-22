## Why

The package now supports runtime bootstrap and artifact initialization, but Stage 1 still has no formal deterministic intake step after those actions complete. Another agent can create `manuscript-profile.json`, yet it still lacks a built-in way to read the source file, record basic source statistics, and write a stable preview before semantic analysis begins.

## What Changes

- Add a deterministic Stage 1 intake script at `paper-condenser/scripts/stage1_intake.py`.
- Read supported text-based source files from the existing `manuscript-profile.json` metadata.
- Write deterministic intake fields back into `manuscript-profile.json`.
- Update the manuscript profile template and protocol documentation to include intake-layer fields.
- Update the skill instructions so file-path workflows run Stage 1 intake before semantic analysis.

## Capabilities

### New Capabilities

- `stage1-intake-bootstrap`: Execute a deterministic Stage 1 intake step for Markdown and plain-text manuscript files by reading source content and updating `manuscript-profile.json` with preview and source statistics.

### Modified Capabilities

None.

## Impact

Affected areas:
- `openspec/changes/bootstrap-stage1-intake/`
- `paper-condenser/scripts/`
- `paper-condenser/assets/artifact-templates/`
- `paper-condenser/references/artifact-protocol.md`
- `paper-condenser/SKILL.md`

No new runtime artifact is added, and no semantic manuscript inference is introduced.
