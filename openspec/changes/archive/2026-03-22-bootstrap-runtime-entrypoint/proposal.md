## Why

The package now has a stable artifact protocol, a template set, and a deterministic initialization script, but it still lacks a formal first-stage runtime entrypoint for file-based manuscript inputs. Another agent still has to manually decide the slug, compute the artifact root, run initialization, and write the first deterministic metadata into `manuscript-profile.json`.

## What Changes

- Add a formal runtime bootstrap script for file-path inputs.
- Generate `document-slug` from the source file name and create `artifacts/<document-slug>/`.
- Reuse the existing artifact initialization logic instead of duplicating it.
- Seed `manuscript-profile.json` with deterministic source metadata after workspace initialization.
- Update the skill instructions so file-path workflows begin with the new runtime bootstrap entrypoint.

## Capabilities

### New Capabilities

- `runtime-entrypoint-bootstrap`: Bootstrap a task-local artifact workspace from a manuscript file path by deriving the slug, initializing artifacts, and seeding deterministic manuscript metadata.

### Modified Capabilities

None.

## Impact

Affected areas:
- `openspec/changes/bootstrap-runtime-entrypoint/`
- `paper-condenser/scripts/`
- `paper-condenser/SKILL.md`

The existing artifact protocol, template set, and low-level initialization script remain in place.
