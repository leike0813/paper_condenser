# Design

## Summary

本次改动只调整 workflow stage 归属、gate 顺序和文档映射，不改 payload schema，不改 `style_profile` 表结构，不改 `08-style-profile.md` 的渲染语义。

## Workflow Reshaping

新的正式 workflow 固定为：

- `stage_0_bootstrap`
- `stage_1_intake_and_inventory`
- `stage_2_manuscript_analysis`
- `stage_3_target_settings`
- `stage_4_condensation_plan`
- `stage_5_final_drafting`
- `stage_6_completed`

其中 Stage 3 的 gate 顺序固定为：

1. `persist_target_settings_basics`
2. `persist_content_selection_board`
3. `confirm_content_selection`
4. `persist_style_profile`
5. `finalize_target_settings`

`persist_style_profile` 本身保持独立动作，但其 `pending_confirmations` 与 gate 归属并入 `stage_3_target_settings`。

## Runtime Boundary

- `style_profile` 表继续保留。
- `08-style-profile.md` 继续保留。
- `persist_condensation_plan` / `confirm_condensation_plan` / `persist_section_rewrite_plan` / `confirm_section_rewrite_plan` 归入新的 `stage_4_condensation_plan`。
- `prepare_section_drafting` / `persist_section_draft` / `approve_section_draft` / `persist_output_target` / `render_final_output_bundle` 归入新的 `stage_5_final_drafting`。

## Documentation Alignment

这次改动要求同步更新：

- `SKILL.md`
- `stage3-playbook.md`
- `stage4-playbook.md`
- `stage5-playbook.md`
- `stage-workflow.md`
- `gate-and-stage-runtime.md`
- `runtime-database-contract.md`
- `artifact-protocol.md`
- `supporting-elements-playbook.md`
- `rewrite-report-playbook.md`
- `README.md`

`stage6-playbook.md` 将退场，因为新的 `stage_6_completed` 不需要独立 playbook。
