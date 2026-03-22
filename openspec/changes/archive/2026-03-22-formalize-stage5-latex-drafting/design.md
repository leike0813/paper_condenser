## Context

The package already has deterministic runtime bootstrap, artifact initialization, Stage 1 intake, and detailed Stage 1-4 playbooks. The remaining gap is that final drafting is still described at a high level and is not anchored to a persisted output file. At the same time, the user has chosen a LaTeX-centered workflow: the formal source is a single `.tex` manuscript file, and the formal output should be a single compilable `.tex` condensed draft. This change therefore needs to tighten both the Stage 5 recipe and the package-wide I/O contract.

## Goals / Non-Goals

**Goals:**
- Turn Stage 5 into a concrete LaTeX drafting playbook with explicit substeps
- Define `artifacts/<document-slug>/final-draft.tex` as the runtime truth for the final draft
- Add built-in single-file LaTeX presets selectable in Stage 2
- Extend deterministic intake to accept `.tex` sources without introducing semantic parsing
- Add a minimal deterministic helper for Stage 5 preflight and final-draft initialization

**Non-Goals:**
- Support multi-file LaTeX projects
- Support external template paths
- Automatically compile or validate the generated LaTeX with `pdflatex`
- Replace the four core intermediate artifacts with a different state model

## Decisions

- Narrow the formal input contract to a single UTF-8 `.tex` file path.
- Keep the existing runtime bootstrap entrypoint and artifact layout.
- Extend `target-settings.json` with a single new field, `latex_template_id`, instead of creating a separate template-selection artifact.
- Add three built-in preset templates under `assets/latex-templates/`:
  - `generic-article`
  - `generic-cn-journal`
  - `generic-en-journal`
- Keep `generic-en-journal` as the stable template id, but switch its implementation to an `elsarticle` single-file skeleton.
- Keep the presets as single-file LaTeX skeletons so Stage 5 can initialize `final-draft.tex` directly from a selected preset.
- Extend `stage1_intake.py` to support `single_file:tex`, but keep its behavior purely deterministic: read UTF-8 text, compute preview and statistics, and write them back to `manuscript-profile.json`.
- Add `scripts/init_final_draft.py` as a minimal helper that validates Stage 5 preconditions and copies the selected preset to `final-draft.tex` without generating prose.
- Represent Stage 5 completeness through the existence and content of `final-draft.tex` plus the existing Stage 1-4 gates, rather than introducing a fifth status artifact.
- Add a dedicated `references/stage5-playbook.md` so the main contract stays compact while still making Stage 5 operationally precise.

## Risks / Trade-offs

Constraining the formal workflow to single-file LaTeX simplifies the runtime contract and keeps the skill aligned with the user's chosen direction, but it excludes more realistic multi-file journal projects. That trade-off is acceptable for the first formal LaTeX version because the skill's main risk is inconsistent execution behavior, not limited template sophistication. Similarly, keeping the new helper script limited to preflight and skeleton initialization avoids over-scriptifying Stage 5, but it means final quality still depends on disciplined LLM drafting and review rather than automated TeX validation.
