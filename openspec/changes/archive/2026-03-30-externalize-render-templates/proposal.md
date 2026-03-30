## Why

The runtime currently renders all six read-only Markdown views from Python string concatenation inside `runtime_core.py`. That couples presentation with runtime business logic, makes template changes require code edits, and leaves the package without explicit render-template assets even though the contract already treats the views as rendered outputs.

## What Changes

- Add a dedicated Jinja2 render-template layer under `paper-condenser/assets/render-templates/`
- Refactor runtime rendering so `runtime_core.py` prepares view-models and delegates Markdown rendering to a separate module
- Update skill documentation so the render-template layer is part of the formal runtime contract

## Capabilities

### New Capabilities

- `render-template-layer-clarification`: The runtime exposes explicit external templates for all six read-only Markdown views.

### Modified Capabilities

- `database-ssot-gate-runtime`: Runtime view rendering is no longer hardcoded in Python and must fail loudly when required templates are missing or broken.

## Impact

- The SQLite database remains the only runtime source of truth.
- Gate/stage interfaces and DB schema stay unchanged.
- Rendered view structure becomes easier to evolve without touching runtime business logic.
