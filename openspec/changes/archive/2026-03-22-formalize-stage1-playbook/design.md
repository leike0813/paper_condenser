## Context

The package already has enough scripting support to initialize a task workspace and perform deterministic intake, but the semantic Stage 1 workflow still relies on agent interpretation of broad instructions. The next risk is inconsistent manuscript understanding, where one agent asks target-setting questions too early, another leaves open questions only in chat, and a third advances to Stage 2 without a stable `manuscript-profile.json`.

## Goals / Non-Goals

**Goals:**
- Turn Stage 1 from a high-level description into a concrete playbook
- Make `manuscript-profile.json` the explicit Stage 1 source of truth
- Define what counts as a usable Stage 1 draft before Stage 2 starts
- Keep the current script chain and interfaces unchanged

**Non-Goals:**
- Add new scripts
- Extend support beyond file-path input
- Introduce a fifth artifact
- Redesign Stage 2 through Stage 5 in this change

## Decisions

- Narrow the formal input contract to file-path input only.
- Keep deterministic preparation exactly as three existing responsibilities:
  - `bootstrap_runtime.py` for task bootstrap
  - `init_artifacts.py` for artifact repair/completion
  - `stage1_intake.py` for deterministic intake
- Treat everything after deterministic intake as LLM-only Stage 1 work.
- Keep Stage 1 truth in `manuscript-profile.json`; do not create a separate Stage 1 working artifact.
- Add a dedicated `references/stage1-playbook.md` so Stage 1 can be precise without overloading the main `SKILL.md`.
- Use `status = analysis_complete` as the Stage 1 completion marker once the minimum usable draft exists.
- Allow unresolved but non-blocking questions to remain, but require them to be written into `open_questions`.

## Risks / Trade-offs

Restricting the first supported workflow to file-path input reduces flexibility, but it removes ambiguity and aligns the contract with the scripts that already exist. The trade-off is worthwhile because this change is about execution reliability, not broadening entry modes.
