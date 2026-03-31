# Design

## Summary

本次改动不调整 DB schema、不新增 workflow stage、不改变任何 action 名称。核心是重新分配“流程说明”和“payload 细节”的承载位置。

## `SKILL.md` Compression Strategy

`SKILL.md` 继续承担：

- skill 目标与非目标
- gate-driven runtime 模型
- Stage 0-6 的自然语言说明
- action 的语义摘要
- references 的按需加载指引

`SKILL.md` 不再承担：

- 各 action 的 payload 字段清单
- 逐字段 payload 说明

Action Summary 中每个 action 只保留：

- 动作含义
- 是否需要 payload
- payload 应优先去哪里看

## Payload Example Surfacing

payload 的具体形态改由两层提供：

1. gate 返回的 `next_action_payload_example`
2. 对应 stage playbook 中的 `Minimal Payload Example`

gate 的样例定位为“最小可执行 JSON 样例”：

- 对无 payload 动作返回 `null`
- 对有 payload 动作返回最小 JSON 对象
- 不追求覆盖所有可选字段

这样 Agent 执行时的默认顺序变为：

1. 读 `SKILL.md` 理解当前阶段和动作语义
2. 跑 gate 获取 `next_action`
3. 先看 `next_action_payload_example`
4. 若仍不确定，再按需读对应 `stageN-playbook.md`

## Playbook Payload Format

需要 payload 的 stage playbook 统一改成：

- `Minimal Payload Example`
- `Notes`

纯脚本动作统一写为：

- `No payload; only --artifact-root`

这样 playbook 不再只告诉 Agent “有哪些字段”，而是直接给出最小可执行样例。
