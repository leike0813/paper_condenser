## Why

`paper-condenser` 目前仍以多个运行态文件作为直接真源，阶段门禁依赖 `SKILL.md` 与分散脚本约束。这种模式在真实测试中容易出现以下问题：

- Agent 直接编辑工件文件，导致状态漂移。
- 阶段推进缺少统一 gate，恢复与继续执行依赖上下文记忆。
- 中间工件既承担真源又承担人类阅读职责，格式和边界不断膨胀。
- 最终输出与中间分析之间缺少统一的状态机与持久化运行时。

为了让 skill 能持续演进，需要把运行态收口为单 SQLite 真源，并以 gate-driven 方式统一下一步动作、门禁、恢复和只读视图渲染。

## What Changes

- 新增单 SQLite 运行态真源：`.paper-condenser-tmp/<document-slug>/paper-condenser.db`
- 新增统一运行时入口：
  - `paper-condenser/scripts/gate_runtime.py`
  - `paper-condenser/scripts/stage_runtime.py`
- 将四个中间工件重构为只读 Markdown 视图，不再作为运行态真源。
- 将 Stage 1-5 的推进方式改为“gate-first -> stage write -> re-gate -> re-render”
- 保留 `final-draft.tex` 与 `rewrite-report.md` 作为最终交付文件，但改为数据库渲染结果。
- 重写主契约与 playbook，使其转向 Database SSOT & gate-driven 范式。

## Capabilities

### New Capabilities

- `database-ssot-gate-runtime`: Define a single SQLite runtime source of truth with strict gate-driven progression, read-only rendered views, and DB-rendered final outputs.

### Modified Capabilities

- `stage1-playbook-clarification`: Stage 1 becomes a gated DB write flow with deterministic intake and supporting-elements inventory persisted to SQLite.
- `stage2-playbook-clarification`: Stage 2 target-setting moves from file editing to DB-backed persistence with explicit pending confirmations.
- `stage3-playbook-clarification`: Stage 3 style profiling becomes DB-backed and render-only for human-readable views.
- `stage4-playbook-clarification`: Stage 4 condensation planning becomes DB-backed and gate-controlled.
- `stage5-playbook-clarification`: Stage 5 final drafting and rewrite-report generation become DB-backed render outputs rather than file-level runtime truth.
- `supporting-elements-flow-clarification`: Supporting-elements inventory and downstream decisions become DB-backed and rendered through gate.
- `rewrite-report-output-clarification`: Rewrite report becomes a DB-rendered final output.

## Impact

- This is a breaking runtime refactor. The old multi-file runtime-truth workflow is no longer the primary execution model.
- Existing helper scripts may remain as compatibility wrappers or deprecated shims, but `SKILL.md` will only expose the gate/stage runtime surface.
- The package becomes closer in architecture to `review-master` and `literature-digest`, making future evolution easier.
