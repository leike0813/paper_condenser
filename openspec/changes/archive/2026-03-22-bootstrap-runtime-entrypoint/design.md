## Context

The skill has already separated deterministic initialization from semantic analysis, but the first-stage entrypoint is still fragmented across human decisions and two separate mental steps. File-path input is the dominant concrete starting point, so the package should expose one formal bootstrap operation for that scenario.

## Goals / Non-Goals

**Goals:**
- Add a single runtime bootstrap entrypoint for file-path inputs
- Formalize slug derivation and artifact-root selection
- Reuse existing initialization logic instead of duplicating it
- Seed only deterministic source metadata in `manuscript-profile.json`

**Non-Goals:**
- Support raw text input
- Support directory inputs or multi-file projects
- Auto-resolve slug collisions with suffixes
- Perform any semantic manuscript analysis during bootstrap

## Decisions

- The script path is fixed at `paper-condenser/scripts/bootstrap_runtime.py`.
- The CLI uses one required argument: `--source-path`.
- `document-slug` is derived from the source file stem and normalized to hyphen-case.
- The artifact root is always `artifacts/<document-slug>/`.
- If the target artifact root already exists, bootstrap fails fast instead of guessing a new name.
- The script reuses functions from `init_artifacts.py` rather than reimplementing template copying.
- Seeded metadata is limited to deterministic fields: `source_id`, `source_path`, `source_type`, `scope`, and `status`.

## Risks / Trade-offs

Limiting bootstrap to file paths keeps the entrypoint narrow and predictable, but it leaves raw-text and directory-based sources for later changes. This is acceptable because those inputs need separate policy decisions, while file-path bootstrap already unlocks a concrete, testable workflow.
