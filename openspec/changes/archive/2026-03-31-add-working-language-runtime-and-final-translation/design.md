# Design

## Decisions

- `working_language` / 初始 `target_language` 并入 `target_settings`
- Stage 2 新增 `confirm_language_context`，并在非 `zh/en` 时追加 `persist_runtime_template_translation`
- Stage 3 的 `persist_target_settings_basics` 不再接收 `target_language`；它根据 form/template 覆盖 Stage 2 初值
- 只读视图运行时模板从 skill 包固定目录切换为“工作区模板副本优先”
- final drafting 新增 `persist_translated_sections`；`render_final_output_bundle` 只装配 translated sections

## Runtime Shape

- Stage 2 顺序：
  - `confirm_language_context`
  - `persist_runtime_template_translation`（按需）
  - `persist_manuscript_analysis`
  - `persist_raw_scope_segments`
  - `persist_semantic_source_units`
- Stage 5 顺序：
  - section loop
  - `persist_output_target`
  - `persist_translated_sections`
  - `render_final_output_bundle`

## Template Strategy

- English 继续作为包内基础模板集
- 新增 Chinese 预置模板集
- 工作区模板副本目录固定为 `.paper-condenser-tmp/<slug>/render-templates/`
- 语言上下文确认后，后续所有只读视图渲染都只读工作区模板副本
