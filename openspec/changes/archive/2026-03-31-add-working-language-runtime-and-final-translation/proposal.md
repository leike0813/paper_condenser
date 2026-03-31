# add-working-language-runtime-and-final-translation

## Why

当前 runtime 只有 `target_language`，没有单独的 `working_language`。这导致：

- 中间工件和 section 草稿没有统一的工作语言约束
- 模板渲染只能固定读取 skill 包模板，不能根据工作语言切换
- 最终 bundle 渲染前没有独立翻译步骤，难以保证“工作语言写作、目标语言交付”的边界

## What Changes

- 在 Stage 2 增加语言上下文确认与工作区模板副本初始化
- 把运行态文本内容统一收口到 `working_language`
- 让 Stage 3 根据最终体例/模板覆盖 `target_language`
- 在 final drafting 中新增独立的 translated-sections 持久化动作，再由 assembly-only 脚本组装最终稿

## Capabilities

- `database-ssot-gate-runtime`
- `self-contained-skill-instructions`

## Impact

- 影响 gate 输出、Stage 2 / 3 / 5 动作语义、运行时模板加载链路和最终 bundle 组装输入
- 不改变 SQLite 作为 SSOT 的总体范式
