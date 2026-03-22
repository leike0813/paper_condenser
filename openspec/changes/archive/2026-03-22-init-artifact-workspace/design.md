## Context

The package now has a stable runtime artifact protocol and a stable template set, but the transition from package templates to live task state still relies on manual copying. That step is deterministic and repetitive, so it should become an explicit script responsibility rather than an implicit agent habit.

## Goals / Non-Goals

**Goals:**
- Add a deterministic artifact initialization script
- Keep the script interface narrow and easy for the skill to call
- Ensure re-running initialization is safe for partially initialized workspaces
- Make the initialization step explicit in `SKILL.md`

**Non-Goals:**
- Derive `document-slug` from manuscript inputs
- Add interactive prompts or semantic decisions to the script
- Overwrite existing runtime artifacts
- Add any workflow logic beyond copying missing templates

## Decisions

- The script path is fixed at `paper-condenser/scripts/init_artifacts.py`.
- The CLI takes a single required target argument via `--artifact-root`.
- The script locates templates relative to the package root so it stays relocatable inside the package.
- If the target directory exists, the script fills missing files and reports already-present files through `skipped_files`.
- stdout is reserved for success-path JSON output so the calling agent can consume it directly.
- Errors are treated as hard failures with non-zero exit codes instead of partial-best-effort initialization.

## Risks / Trade-offs

Requiring an explicit `--artifact-root` keeps the script simple and predictable, but it leaves slug derivation in the agent workflow for now. That trade-off is intentional because slug generation is still partly user-facing and may need separate policy decisions later.
