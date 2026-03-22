## Context

The repository is for developing an Agent Skill rather than a conventional application. The intended publishable deliverable is a Skill package named `paper-condenser`, but the package directory currently has no content. The repository root already contains project guidance and reference documents that support development, not final package layout.

## Goals / Non-Goals

**Goals:**
- Bootstrap a publishable Skill package at `paper-condenser/`
- Add the minimum required metadata for discovery and invocation
- Reserve internal directories for future references, scripts, and assets
- Keep the first version intentionally small and structurally correct

**Non-Goals:**
- Write the full production-grade Skill instructions
- Migrate or duplicate the existing repository-root reference documents into the package
- Add helper scripts or other business logic
- Introduce icons, brand metadata, external dependencies, or extra assets

## Decisions

- Use the existing `paper-condenser/` subdirectory as the package root instead of the repository root.
- Keep `paper-condenser/SKILL.md` minimal but valid, with four sections only: `Overview`, `Hard Constraints`, `Workflow`, and `Resources`.
- Encode the public invocation name as `paper-condenser` in frontmatter and reference `$paper-condenser` explicitly in the UI metadata prompt.
- Limit `paper-condenser/agents/openai.yaml` to the `interface` block to avoid premature dependency declarations.
- Preserve `references/`, `scripts/`, and `assets/` with placeholder files so the directory layout survives version control before substantive content is added.

## Risks / Trade-offs

This bootstrap leaves the package intentionally incomplete in terms of workflow depth and reference material, so future changes must expand the skill instructions before the package is practically useful. The trade-off is acceptable because this change is only meant to establish a valid package skeleton without making broader content decisions.
