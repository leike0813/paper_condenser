# add-runtime-digest-to-gate

## Why

当前 `paper-condenser` 的 gate 返回已经能给出 `next_action` 和 `next_action_payload_example`，但在上下文较长、阶段切换频繁或跨轮恢复执行时，Agent 仍然容易忘记 skill 的核心纪律，只记得局部 action，而丢失“先 gate、后执行、按需读 playbook、最终合成只做 assembly”等全局约束。

`review-master` 的实践表明，给 gate 返回一份稳定的 runtime digest，可以显著降低这种执行漂移。

## What Changes

- 新增独立静态资产 `paper-condenser/assets/runtime/skill-runtime-digest.md`
- gate 返回新增顶层字段 `runtime_digest`
- `runtime_digest` 的内容固定来自独立资产文件，不从 `SKILL.md` 动态解析
- `SKILL.md` 与 `gate-and-stage-runtime.md` 同步说明新的读取顺序

## Impact

- Agent 在首次进入后，后续恢复时可以直接从 gate 返回中重获核心纪律提醒
- 不需要引入 `resume_packet` 或新的恢复包结构
- 不改变 DB schema、不改变 action 名称、不改变只读视图集合
