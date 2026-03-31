## Context

当前运行态只读视图的编号来自多轮增量追加，而不是从当前 workflow 重新设计。结果是 Stage 1 的 supporting-elements inventory、Stage 2 的 source-layer 视图、Stage 3 的 content-selection board 都被排到了不自然的位置，导致 Agent 和用户在浏览 artifact root 时无法直接按文件编号理解流程顺序。

这次变更不会改数据库 schema，也不会改 gate/stage 动作，只会重排渲染视图的文件名与模板文件名，并同步所有文档引用。

## Goals / Non-Goals

**Goals:**

- 让只读 Markdown 视图编号严格对应 workflow 阅读顺序。
- 让 `runtime_core.py` 的 `RENDERED_VIEWS` 和 `runtime_rendering.py` 的模板映射保持一致。
- 让 `SKILL.md` 与 `references/` 中的视图引用全部切到新的编号体系。
- 一次性完成全量重排，避免留下新旧编号并存的过渡语义。

**Non-Goals:**

- 不修改 SQLite schema。
- 不改变任何 stage 的 gate 规则、动作名称或运行时状态机。
- 不修改 `section-reviews/<section_order>-<section_id>.md` 的目录结构。
- 不引入视图别名、兼容双命名或运行时自动迁移逻辑。

## Decisions

### 1. 按 workflow 顺序整体重排，而不是做局部修补

采用完整重排，而不是只挪动个别编号。

新的编号固定为：

1. `01-agent-resume.md`
2. `02-manuscript-profile.md`
3. `03-supporting-elements-inventory.md`
4. `04-scope-segments.md`
5. `05-semantic-source-units.md`
6. `06-target-settings.md`
7. `07-content-selection-board.md`
8. `08-style-profile.md`
9. `09-condensation-plan.md`
10. `10-section-rewrite-plan.md`
11. `11-section-drafting-board.md`

这样编号与 Stage 1 → Stage 6 的阅读顺序一致，不再混入历史追加顺序。

### 2. 模板文件名与输出文件名同步重排

Jinja2 模板文件名和渲染输出文件名都采用相同编号，不保留旧模板编号。

这样可以让：

- `runtime_rendering.py` 的固定映射保持直观；
- `artifact-protocol.md` 的模板映射保持一眼可核对；
- 后续维护时不用在“视图逻辑顺序”和“模板历史编号”之间做脑内映射。

### 3. 不做兼容双命名

不保留旧文件名副本，也不在运行时同时输出新旧两套编号。

原因：

- 这次调整是阅读顺序纠偏，不值得引入双命名复杂度。
- 双命名会让文档长期漂移，继续污染主契约。
- 运行态视图是只读渲染结果，不是稳定外部 API，接受一次性改名成本。

## Risks / Trade-offs

- [Risk] 旧 smoke 测试、人工习惯或外部脚本可能还在引用旧文件名 → Mitigation: 全量更新 `SKILL.md`、`artifact-protocol.md`、各 stage playbook 和运行时映射，并通过全局搜索确认无旧编号残留。
- [Risk] 模板重命名后 `runtime_rendering.py` 映射漏改会导致渲染失败 → Mitigation: 同步修改固定映射并运行 `quick_validate`、`mypy` 和最小 gate smoke。
- [Risk] 这次没有做兼容层，旧 workspace 中已有的旧编号渲染文件会显得过时 → Mitigation: 只读视图本来就是可重渲染产物；下次 gate/stage 写入时会生成新的编号文件。
