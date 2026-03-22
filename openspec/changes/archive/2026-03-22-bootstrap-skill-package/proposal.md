## Why

The repository currently contains only project guidance and reference documents, but no publishable Skill package. The reserved `paper-condenser/` directory is still empty, so there is no valid Skill entrypoint, UI metadata, or internal resource layout for downstream use.

## What Changes

- Create the initial OpenSpec artifacts for bootstrapping a publishable Skill package.
- Initialize `paper-condenser/` as the Skill package root instead of using the repository root.
- Add a minimal but valid `SKILL.md` and `agents/openai.yaml`.
- Reserve `references/`, `scripts/`, and `assets/` inside the package for future incremental work.
- Keep the repository root `references/` directory unchanged and outside the package boundary for now.

## Capabilities

### New Capabilities

- `skill-package-bootstrap`: Establish a publishable `paper-condenser` Skill package with required metadata files and placeholder resource directories.

### Modified Capabilities

None.

## Impact

Affected areas:
- `openspec/changes/bootstrap-skill-package/`
- `paper-condenser/`

No external dependencies, runtime integrations, or existing repository references are modified in this change.
