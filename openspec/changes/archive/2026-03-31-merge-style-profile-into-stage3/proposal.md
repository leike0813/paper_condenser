# merge-style-profile-into-stage3

## Why

当前 runtime 把 `persist_style_profile` 单独放在 `stage_4_style_profile`，导致用户视角下的“目标设置阶段”被拆成了两段：先做基本设置与内容取舍，再突然切到一个独立的风格阶段。这会削弱 Stage 3 作为统一目标设置阶段的完整性，也让后续的 stage 编号和 playbook 文件名显得不够自然。

## What Changes

- 将 `persist_style_profile` 正式并入 `stage_3_target_settings`，位置固定在内容取舍确认之后、最终确认之前。
- 将后续 workflow stage 前移：
  - `stage_4_condensation_plan`
  - `stage_5_final_drafting`
  - `stage_6_completed`
- 保留 `style_profile` 表和 `08-style-profile.md` 视图，不合并真源，只调整 gate 顺序和阶段归属。
- 同步重排 `SKILL.md`、stage playbook 和 references 中的阶段叙述与文件映射。

## Impact

- Stage 3 将成为真正完整的“目标设置 + 内容取舍 + 风格画像 + 最终确认”阶段。
- 用户不会再感知到一个割裂的独立风格 stage。
- workflow stage、playbook 文件名和 `SKILL.md` 中的阶段描述会重新保持一致。
