# Design

## Summary

本次改动不新增 workflow stage，只细化 `stage_5_condensation_plan` 与 `stage_6_final_drafting` 的动作和门禁。

## Stage 5 Approval Model

Stage 5 固定拆成两层计划：

1. 整体 condensation plan
2. 详细 section rewrite plan

每一层都必须先写草案，再通过独立的 confirm action 获得用户批准。运行时 gate 顺序固定为：

1. `persist_condensation_plan`
2. `confirm_condensation_plan`
3. `persist_section_rewrite_plan`
4. `confirm_section_rewrite_plan`

任何一层若被退回修改，gate 都必须回到对应的 persist action。

## Section Rewrite Plan Enrichment

每个 section rewrite plan item 不再只是“字数 + 来源绑定”，而要成为用户可审的成稿预演。每节至少需要：

- `section_summary`
- `section_strategy`
- `figure_table_usage`
- `reference_usage`
- `aux_usage_rationale`（仅当使用 aux-backed semantic units 时强制）

这样 `09-section-rewrite-plan.md` 才能让用户大致想象最终稿会如何组织。

## Assembly-only Final Bundle

`render_final_output_bundle` 保持脚本实现，但其职责边界收紧为：

- 只装配已批准的 section drafts
- 套用 LaTeX 模板
- 复制实际引用图片
- 改写图像路径
- 生成 rewrite report

它不允许：

- 改写 section 正文
- 新增 section-level 实质性内容
- 在最终渲染时润色或重组论述

## Documentation Impact

`SKILL.md` 与 Stage 5/6 playbook 需要显式写出：

- Stage 5 结束不等于开始写稿
- Stage 6 的入口前提是“两层计划都经过用户批准”
- 最终 bundle 渲染是 assembly-only
