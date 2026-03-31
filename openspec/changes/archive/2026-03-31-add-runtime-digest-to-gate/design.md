# Design

## Summary

本次改动采用最小增量方案：新增一份静态 runtime digest 资产，并让 gate 以顶层字符串字段返回它。

## Runtime Digest Source

digest 固定存放在：

- `paper-condenser/assets/runtime/skill-runtime-digest.md`

它是一个手工维护的独立摘要资产，不从 `SKILL.md` 动态提取。这样可以避免运行时解析脆弱性，并允许 digest 保持比 `SKILL.md` 更短、更适合恢复场景。

## Gate Output Contract

在现有 gate 结果上新增：

- `runtime_digest: string`

规则固定为：

- 返回 digest 的完整文本内容
- 不返回文件路径
- `--source-path` 和 `--artifact-root` 两种入口都必须返回相同的 digest
- bootstrap 场景同样返回 digest

## Documentation Positioning

- `SKILL.md` 继续是首次阅读入口
- 后续恢复执行时，优先看 gate 返回的 `runtime_digest`
- 再看 `next_action` 与 `next_action_payload_example`
- 若仍有疑问，再按需读取对应 playbook

本次不引入 `resume_packet`，也不要求把 digest 渲染进 `01-agent-resume.md`
