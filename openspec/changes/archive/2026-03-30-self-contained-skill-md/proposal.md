## Why

`paper-condenser/SKILL.md` 目前已经包含 runtime 入口、状态机和 action 协议，但它仍然偏“协议摘要”，不够像一份首次执行即可依赖的主指令。Agent 很容易在开始时就去读多个 `references/` 文档，才能理解这个 skill 的总体目标、各阶段在做什么、为什么这样做，以及什么时候需要向用户确认。

这会带来两个问题：

- 首次进入成本偏高，容易浪费 context。
- 主契约与补充文档之间的主次关系不够清楚，Agent 容易把 `references/` 当作默认必读全集。

因此需要把 `SKILL.md` 重构为一份自包含、完整但精简的主指令：默认只读它，就应知道总体上该做什么、按什么顺序做、每一阶段的目标和完成标准是什么；只有遇到困难、歧义或需要更细的 payload / gate 规则时，才按需读取对应 reference。

## What Changes

- 重写 `paper-condenser/SKILL.md`，补足：
  - skill mission、适用场景与非目标
  - working style 与决策边界
  - 明确的 “read `SKILL.md` first / references on demand” 策略
  - Stage 0-6 的自然语言说明：做什么、怎么做、不要做什么、完成标志
  - action summary 的用途化说明，而不仅是字段清单
- 轻量更新 `references/stage-workflow.md` 与 `references/gate-and-stage-runtime.md`，明确它们是补充说明，不是首次执行入口。

## Capabilities

### New Capabilities

- `self-contained-skill-instructions`: 要求 `SKILL.md` 本身足以作为首次执行的完整主指令，并明确 references 采用按需加载策略。

### Modified Capabilities

- `database-ssot-gate-runtime`: 主契约的叙事方式从“协议优先”升级为“主说明优先 + 协议摘要补充”。

## Impact

- Agent 默认只需读取 `SKILL.md` 就能启动工作。
- `references/` 继续保留，但定位变成按需加载的补充材料。
- 不改 runtime 行为，不改 DB schema，不改 gate/stage 状态机。
