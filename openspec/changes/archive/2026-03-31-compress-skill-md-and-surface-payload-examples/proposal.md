# compress-skill-md-and-surface-payload-examples

## Why

当前 `SKILL.md` 已经超过 500 行，冗余主要集中在 `Action Summary` 对 payload 键名的逐项罗列。这类信息既不适合作为首次阅读内容，也不利于 Agent 快速理解流程主线。

与此同时，gate 虽然会返回唯一允许的 `next_action`，但不会同时给出下一步动作的最小 payload 形态。结果是 Agent 要么回头翻完整个 stage playbook，要么凭记忆构造 payload，都会增加上下文浪费和执行偏差。

## What Changes

- 压缩 `SKILL.md`，保留主流程、阶段目的、动作含义和执行纪律，但删除逐动作 payload 字段清单。
- 将 payload 的具体形态下沉到对应 stage playbook，并统一为最小 JSON 样例。
- 扩展 gate 返回，新增 `next_action_payload_example`，与 `next_action` 一起提供下一步动作的最小 payload 样例。

## Impact

- `SKILL.md` 更适合首次阅读，Agent 不需要先消化大量 payload 细节。
- 执行具体动作时，Agent 可以先看 gate 返回的最小 payload 样例，再按需打开 playbook。
- payload 说明的位置更稳定：主流程看 `SKILL.md`，具体形态看 gate / playbook。
