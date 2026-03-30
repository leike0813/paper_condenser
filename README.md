# paper_condenser

`paper_condenser` 是一个 **Agent Skill 开发项目**，目标是构建一个可发布的 Skill 包，帮助 Agent 以**交互式、阶段化**的方式，将长篇学术论文、研究报告或章节转写为符合期刊论文体例的凝缩版文稿。

这不是常规软件工程仓库。它的核心产物不是 Web 服务或库，而是一个位于 [paper-condenser](/home/joshua/Workspace/Code/Skill/paper_condenser/paper-condenser) 的 Skill 包，其中以 [SKILL.md](/home/joshua/Workspace/Code/Skill/paper_condenser/paper-condenser/SKILL.md) 作为主执行契约，并辅以 SQLite gate-driven runtime、确定性 helper scripts、Jinja2 渲染模板、LaTeX 模板资产和参考文档。

## 项目目标

- 分阶段理解用户提供的原稿
- 提炼主题、主要工作、创新点和结构信息
- 通过数据库真源持久化原稿理解、目标设置、风格画像和凝缩方案
- 与用户交互式确认关键决策，而不是替用户做决定
- 仅在前置阶段全部完成后，生成最终 LaTeX 凝缩稿

## 非目标

- 不一步到位直接产出最终论文
- 不替用户决定语言、体例、目标期刊、篇幅或重点取舍
- 不直接修改用户原稿
- 不用脚本替代 LLM 的语义理解和写作判断

## 发布包

正式 Skill 包位于 [paper-condenser](/home/joshua/Workspace/Code/Skill/paper_condenser/paper-condenser)。

其中最重要的内容是：

- [SKILL.md](/home/joshua/Workspace/Code/Skill/paper_condenser/paper-condenser/SKILL.md)：主执行契约
- [agents/openai.yaml](/home/joshua/Workspace/Code/Skill/paper_condenser/paper-condenser/agents/openai.yaml)：Agent 接口元数据
- [references](/home/joshua/Workspace/Code/Skill/paper_condenser/paper-condenser/references)：分阶段 playbook、工件协议和论文写作规范参考
- [scripts](/home/joshua/Workspace/Code/Skill/paper_condenser/paper-condenser/scripts)：确定性辅助脚本
- [assets](/home/joshua/Workspace/Code/Skill/paper_condenser/paper-condenser/assets)：中间工件渲染模板与 LaTeX preset

## 当前实现状态

当前 Skill 已切换到 **Database SSOT & gate-driven** 范式，已经具备这些能力：

- 单文件 `.tex` 原稿路径输入
- 单 SQLite 运行态真源：`.paper-condenser-tmp/<document-slug>/paper-condenser.db`
- `gate_runtime.py` + `stage_runtime.py` 双入口
- Stage 1 到 Stage 6 的 gate-driven 状态机
- Stage 2 的 `main_scope + aux_scopes` 双层范围模型
- 十个只读 Markdown 视图由外部 Jinja2 模板渲染
- Stage 6 的 section-loop drafting / count validation / user approval
- 最终 bundle 的 DB-rendered `final-draft.tex` 与 `rewrite-report.md`
- 内置 LaTeX 模板 preset，包括通用 article、中文期刊和基于 `elsarticle` 的英文期刊模板

运行态文件默认不会写入 Skill 包目录，而是写入当前项目目录下的 `.paper-condenser-tmp/`。

当前设计中，脚本只负责确定性工作，例如：

- SQLite schema 初始化
- gate 判定与 `next_action` 输出
- source intake 与 supporting-elements inventory 提取
- raw main/aux scope segmentation
- semantic source unit consolidation 的结构化写库
- 只读视图渲染
- 中间工件 Jinja2 模板渲染
- 最终输出文件渲染

语义理解、用户提问、方案判断和正文写作仍由 LLM 负责。

## 目录结构

```text
.
├── AGENTS.md
├── README.md
├── references/                    # 仓库级开发参考资料
├── openspec/                      # OpenSpec 变更与归档
└── paper-condenser/               # 正式 Skill 包
    ├── SKILL.md
    ├── agents/
    ├── assets/
    │   ├── render-templates/
    │   └── latex-templates/
    ├── references/
    └── scripts/
```

## 关键文档入口

- 如果你想了解“Skill 怎么执行”，先看 [SKILL.md](/home/joshua/Workspace/Code/Skill/paper_condenser/paper-condenser/SKILL.md)。
- 如果你想了解“运行态文件与数据库的关系”，看 [artifact-protocol.md](/home/joshua/Workspace/Code/Skill/paper_condenser/paper-condenser/references/artifact-protocol.md)。
- 如果你想了解 runtime DB 和 gate/stage 入口，看：
  - [runtime-database-contract.md](/home/joshua/Workspace/Code/Skill/paper_condenser/paper-condenser/references/runtime-database-contract.md)
  - [gate-and-stage-runtime.md](/home/joshua/Workspace/Code/Skill/paper_condenser/paper-condenser/references/gate-and-stage-runtime.md)
- 如果你想了解每个阶段的细化步骤，看：
  - [stage0-playbook.md](/home/joshua/Workspace/Code/Skill/paper_condenser/paper-condenser/references/stage0-playbook.md)
  - [stage1-playbook.md](/home/joshua/Workspace/Code/Skill/paper_condenser/paper-condenser/references/stage1-playbook.md)
  - [stage2-playbook.md](/home/joshua/Workspace/Code/Skill/paper_condenser/paper-condenser/references/stage2-playbook.md)
  - [stage3-playbook.md](/home/joshua/Workspace/Code/Skill/paper_condenser/paper-condenser/references/stage3-playbook.md)
  - [stage4-playbook.md](/home/joshua/Workspace/Code/Skill/paper_condenser/paper-condenser/references/stage4-playbook.md)
  - [stage5-playbook.md](/home/joshua/Workspace/Code/Skill/paper_condenser/paper-condenser/references/stage5-playbook.md)
  - [stage6-playbook.md](/home/joshua/Workspace/Code/Skill/paper_condenser/paper-condenser/references/stage6-playbook.md)
  - [rewrite-report-playbook.md](/home/joshua/Workspace/Code/Skill/paper_condenser/paper-condenser/references/rewrite-report-playbook.md)
- 如果你想了解中文/SCI 论文体例参考，看：
  - [Chinese_paper_guidance.md](/home/joshua/Workspace/Code/Skill/paper_condenser/paper-condenser/references/Chinese_paper_guidance.md)
  - [SCI_paper_guidance.md](/home/joshua/Workspace/Code/Skill/paper_condenser/paper-condenser/references/SCI_paper_guidance.md)

## 开发资料与运行资料的区别

- 仓库根 [references](/home/joshua/Workspace/Code/Skill/paper_condenser/references) 是开发参考资料。
- 发布包内 [paper-condenser/references](/home/joshua/Workspace/Code/Skill/paper_condenser/paper-condenser/references) 是运行时可被 Skill 正式引用的资料。

不要把仓库根参考目录直接当成 Skill 运行资源。

## 运行态工件位置

- Skill 包本身是静态资产。
- 运行过程中产生的 DB、只读视图与最终稿默认写入当前项目目录下的 `.paper-condenser-tmp/<document-slug>/`。
- 不应把运行态工件写进 [paper-condenser](/home/joshua/Workspace/Code/Skill/paper_condenser/paper-condenser) 包目录内部。

## OpenSpec 状态

本项目此前的实现工作以 OpenSpec change 驱动完成，现有 change 已归档到 [openspec/changes/archive](/home/joshua/Workspace/Code/Skill/paper_condenser/openspec/changes/archive)。

## 适合谁看这份 README

- 想快速理解这个仓库是做什么的开发者
- 想区分“仓库”与“正式发布 Skill 包”的维护者
- 想继续扩展 Stage 流程、脚本或模板资产的后续贡献者

如果你准备继续开发，默认从 [SKILL.md](/home/joshua/Workspace/Code/Skill/paper_condenser/paper-condenser/SKILL.md) 和 [AGENTS.md](/home/joshua/Workspace/Code/Skill/paper_condenser/AGENTS.md) 开始。
