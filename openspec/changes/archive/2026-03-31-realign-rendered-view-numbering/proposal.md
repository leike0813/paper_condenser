## Why

当前只读工件的编号是按历史演进逐步追加出来的，已经不再反映实际 workflow 顺序。继续沿用这套编号会让 Agent 和用户在阅读运行态视图时产生阶段错位感，降低 Stage 1 到 Stage 6 的可读性和可审查性。

## What Changes

- **BREAKING** 重新按 workflow 顺序整体重排只读 Markdown 视图编号。
- 将 supporting-elements inventory、Stage 2 视图、Stage 3 视图、Stage 4 视图、Stage 5 视图、Stage 6 drafting board 重新映射到新的稳定编号。
- 同步更新 Jinja2 渲染模板文件名与固定映射。
- 同步更新 `SKILL.md`、artifact protocol、各 stage playbook 和相关引用，使其全部使用新的视图编号。

## Capabilities

### New Capabilities

- None.

### Modified Capabilities

- `database-ssot-gate-runtime`: Rendered runtime view filenames and ordering now align with workflow stage order.
- `render-template-layer-clarification`: External template filenames and fixed template-to-view mapping change to the new workflow-aligned numbering.
- `self-contained-skill-instructions`: `SKILL.md` must present the rendered-view inventory using the workflow-aligned numbering and references.

## Impact

- Affected code:
  - `paper-condenser/scripts/runtime_core.py`
  - `paper-condenser/scripts/runtime_rendering.py`
- Affected assets:
  - `paper-condenser/assets/render-templates/*.md.j2`
- Affected docs:
  - `paper-condenser/SKILL.md`
  - `paper-condenser/references/*.md`
- Runtime impact:
  - Existing rendered view filenames under artifact roots will change, but DB schema and gate logic remain unchanged.
