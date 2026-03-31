# tighten-stage5-approvals-and-assembly-boundary

## Why

当前 Stage 5 的整体凝缩方案与详细 section rewrite plan 都没有被强制要求用户显式批准。实际运行中，Agent 在完成 Stage 3 之后会继续写入 Stage 4 和 Stage 5，并在未申请计划批准的情况下直接进入 Stage 6 的逐节写作。这会削弱前面各阶段铺垫出来的约束价值。

此外，当前 `09-section-rewrite-plan.md` 还不足以让用户预演最终稿形态，而最终 bundle 渲染虽然实际是脚本动作，但指令层对其 assembly-only 边界写得不够硬。

## What Changes

- 将 Stage 5 调整为“两层计划、两次批准”：
  - `persist_condensation_plan`
  - `confirm_condensation_plan`
  - `persist_section_rewrite_plan`
  - `confirm_section_rewrite_plan`
- 强化 section rewrite plan 的每节内容，要求写明章节摘要、组织策略、图表使用策略、引用使用策略，以及 aux 使用理由。
- 收紧 gate：只有整体 plan 和 section plan 都批准后，才允许进入 Stage 6。
- 明确 `render_final_output_bundle` 是 assembly-only，只允许装配已批准 section drafts，不允许在最终渲染时继续写作或润色。

## Impact

- 运行时 gate 更严格，Stage 6 不会再在计划未批准时被提前激活。
- `09-section-rewrite-plan.md` 将成为真正可供用户审阅的成稿预演视图。
- 最终 bundle 渲染的职责边界更清晰，减少 Agent 在最后一步自由发挥的空间。
