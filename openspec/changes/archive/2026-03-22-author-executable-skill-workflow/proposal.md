## Why

The current `paper-condenser` package is structurally valid but not operational. It explains the goal at a high level, yet it does not tell another agent what inputs it requires, which decisions must be confirmed with the user, what intermediate artifacts must be created, or when drafting is allowed to start.

## What Changes

- Define an executable, artifact-driven workflow for `paper-condenser`.
- Rewrite the package `SKILL.md` from a principle-only summary into an explicit execution protocol.
- Add package-internal references that document stage behavior and artifact contracts.
- Establish the minimum set of four working artifacts needed before final drafting.
- Keep the existing package interface stable and avoid adding helper scripts in this change.

## Capabilities

### New Capabilities

- `interactive-condensation-workflow`: Guide staged manuscript understanding, target-setting, style profiling, and condensation planning through explicit user confirmations and four persistent working artifacts.

### Modified Capabilities

None.

## Impact

Affected areas:
- `openspec/changes/author-executable-skill-workflow/`
- `paper-condenser/SKILL.md`
- `paper-condenser/references/`

No scripts, UI metadata, or repository-root reference files are modified by this change.
