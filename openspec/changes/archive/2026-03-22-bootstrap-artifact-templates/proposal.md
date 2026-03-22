## Why

The skill already defines the runtime artifact set and the rules for using those artifacts, but it still does not ship formal package templates. Another agent can infer what files should exist, yet it still lacks a canonical starting point for creating those files under `artifacts/<document-slug>/`.

## What Changes

- Add a package-owned template set for the four runtime artifacts.
- Place the templates under `paper-condenser/assets/artifact-templates/`.
- Keep the templates minimal, structured, and aligned with the existing artifact protocol.
- Update package documentation to state where the templates live and how they relate to runtime artifact files.
- Avoid adding scripts or changing the public skill interface in this change.

## Capabilities

### New Capabilities

- `artifact-template-bootstrap`: Provide package-owned static templates for the four condensation workflow artifacts so they can be copied into `artifacts/<document-slug>/` as initialization points.

### Modified Capabilities

None.

## Impact

Affected areas:
- `openspec/changes/bootstrap-artifact-templates/`
- `paper-condenser/assets/`
- `paper-condenser/SKILL.md`
- `paper-condenser/references/artifact-protocol.md`

No scripts, OpenAI metadata, or existing workflow contracts are changed.
