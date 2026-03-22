## Context

The previous change defined a four-artifact runtime protocol, but the package still lacks canonical starter files. Without template assets, another agent must construct runtime files ad hoc, which creates avoidable drift from the protocol.

## Goals / Non-Goals

**Goals:**
- Add a package-owned template directory for the four runtime artifacts
- Keep template file names identical to runtime file names
- Keep templates minimal and neutral so they act as initialization points
- Document the relationship between package templates and runtime artifact copies

**Non-Goals:**
- Add initialization scripts
- Add a fifth artifact or change the existing four-artifact model
- Add realistic manuscript examples to the templates
- Change `agents/openai.yaml` or public skill invocation metadata

## Decisions

- Store templates under `paper-condenser/assets/artifact-templates/` because they are output-facing assets meant to be copied into working directories.
- Use exactly four template files, one for each runtime artifact, with identical file names.
- Keep JSON templates aligned with the minimum fields already defined in `references/artifact-protocol.md`.
- Keep Markdown templates limited to required headings plus a small amount of placeholder guidance.
- Mark the approval state in `condensation-plan.md` as not approved by default.
- Add brief documentation in `SKILL.md` and `references/artifact-protocol.md` instead of creating a separate template manual.

## Risks / Trade-offs

Minimal templates are less hand-holding than rich examples, but they avoid biasing the workflow toward a specific paper domain or target journal. This is the right trade-off for a reusable base package; future changes can add initialization automation without changing the template contract.
