## Why

The package now has detailed playbooks for Stages 1 through 4, but Stage 5 is still underspecified and the package still treats the final draft as a conversational outcome rather than a persisted runtime artifact. In addition, the current input contract is still file-path generic while the actual target workflow should center on a single LaTeX manuscript source and a single LaTeX condensed output. Without this change, different agents can interpret Stage 5 differently, skip draft persistence, or continue using Markdown/text assumptions that no longer match the intended workflow.

## What Changes

- Add a dedicated Stage 5 drafting playbook with explicit substeps for preflight, template initialization, section drafting, whole-draft integration, whole-draft review, and fallback decisions.
- Add a minimal helper script for Stage 5 preflight and final-draft skeleton initialization.
- Migrate the package's formal input contract to a single UTF-8 `.tex` manuscript file path.
- Define `artifacts/<document-slug>/final-draft.tex` as the runtime truth for the final condensed manuscript.
- Extend `target-settings.json` with `latex_template_id` and make template choice part of Stage 2 confirmation.
- Add built-in single-file LaTeX preset templates under `assets/latex-templates/`.
- Extend deterministic intake support to `single_file:tex` in `scripts/stage1_intake.py`.

## Capabilities

### New Capabilities

- `stage5-playbook-clarification`: Define an explicit Stage 5 LaTeX drafting recipe, handoff rules, and persisted final-output contract.

### Modified Capabilities

- `stage1-intake-bootstrap`: Extend deterministic intake support to `single_file:tex`.
- `stage2-playbook-clarification`: Make LaTeX preset selection part of confirmed Stage 2 target settings.
- `stage1-playbook-clarification`: Tighten the formal input contract from a generic manuscript file path to a single `.tex` manuscript file path.

## Impact

- Affects the core skill contract in `paper-condenser/SKILL.md`.
- Affects Stage 1 and Stage 2 artifact protocol and playbooks.
- Adds LaTeX preset assets and a new Stage 5 reference file.
- Requires small Python changes in `paper-condenser/scripts/stage1_intake.py` and `paper-condenser/scripts/init_final_draft.py`.
