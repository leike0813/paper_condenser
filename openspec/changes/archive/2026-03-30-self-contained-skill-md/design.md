## Overview

本次 change 只做文档重构，不触碰 runtime 行为。设计目标是让 `paper-condenser/SKILL.md` 具备三种能力：

1. 能让 Agent 在首次进入时快速理解这个 skill 的目标、边界和工作方式。
2. 能让 Agent 仅凭 `SKILL.md` 理解 Stage 0-6 的总体流程与每一步的大方向。
3. 能让 Agent 明确知道：references 不是默认必读全集，而是按需加载的补充材料。

## Design Decisions

### 1. `SKILL.md` 采用“主说明优先”的结构

新的 `SKILL.md` 固定采用这些段落：

- `Mission`
- `Working Style`
- `Reading Strategy`
- `Runtime Model`
- `Stage Overview`
- `Action Summary`
- `Reference Loading Guide`

这样可把“为什么做 / 做什么 / 怎么做”放在前面，把 CLI 与 payload 协议放在后面。

### 2. 每个 stage 在 `SKILL.md` 中都提供最小可执行说明

每个阶段都使用统一格式：

- `Purpose`
- `What To Do`
- `How To Work`
- `Do Not`
- `Done When`

这保证 Agent 在不打开 `stageN-playbook.md` 的前提下，也能掌握阶段目标与工作边界。

### 3. references 明确改成按需加载

`SKILL.md` 会显式声明：

- 默认先只读 `SKILL.md`
- 不要在开始时批量读取 `references/`
- 只有遇到当前阶段的困难、歧义、复杂 payload 设计、gate/blocker、或横切规则时，才去读对应 reference

`stage-workflow.md` 与 `gate-and-stage-runtime.md` 也会补一句定位说明，避免它们被误当成首次执行入口。

## Non-Goals

- 不改 SQLite schema
- 不改 gate / stage action
- 不改渲染模板
- 不把所有 playbook 全文搬进 `SKILL.md`

## Validation

- `openspec validate self-contained-skill-md`
- `quick_validate.py paper-condenser`
- 人工检查：
  - 只读 `SKILL.md` 是否能解释清楚 Stage 0-6
  - 是否显式要求 references 按需加载
  - `stage-workflow.md` / `gate-and-stage-runtime.md` 是否已退回补充定位
