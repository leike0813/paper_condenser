# Design

## Decision

Adopt Jinja2 templates as the only render layer for the six read-only Markdown runtime views.

## Template scope

- Include templates only for:
  - `01-agent-resume.md`
  - `02-manuscript-profile.md`
  - `03-target-settings.md`
  - `04-style-profile.md`
  - `05-condensation-plan.md`
  - `06-supporting-elements-inventory.md`
- Do not template `final-draft.tex` or `rewrite-report.md` in this change.

## Runtime split

- `runtime_core.py`
  - keeps DB schema, gate logic, payload validation, and view-model preparation
  - stops owning Markdown string assembly for intermediate views
- `runtime_rendering.py`
  - owns template discovery, Jinja2 environment creation, rendering, and file writes

## Failure policy

- Missing template file is a hard runtime error.
- Jinja2 syntax/render errors are hard runtime errors.
- No silent fallback to inline Python strings is allowed.

## Mapping

Template lookup is fixed and one-to-one. The runtime must not perform dynamic template discovery or user-selected template overrides for intermediate views.
