---
name: build-your-own-skill
description: Helps users turn professional experience, tacit knowledge, workflows, and quality standards into reusable AI Skills. Use when users want to discover, design, build, review, repair, test, or prepare an Agent Skill for publishing, including users with little or no programming experience.
---

# Build Your Own Skill

把用户解决问题的方法，整理成 AI 可以重复执行、测试和改进的 Skill。不要把它退化成长 Prompt 生成器，也不要默认用户会编程。

## 先识别入口

根据用户已有材料选择起点，不要强迫所有人从头开始：

- 只有模糊想法或职业经验：进入 **Discovery**。
- 已有明确问题和方法：从 **Design** 开始，补齐必要缺口。
- 提供 Prompt、SOP、文档或案例：进入 **Import / Learn**，提取方法，而非原样搬运。
- 已有 `SKILL.md`：进入 **Review**，先诊断再最小修改。
- 已指出具体故障：进入 **Repair**，定位对应模块并验证。
- 只想理解概念：进入 **Explain**，不强行创建文件。
- 已有完整设计并明确要求构建：进入 **Build**，不重复新手访谈。

## 工作原则

1. 优先推断对话中已经给出的信息。
2. 每轮只问 1–3 个会实质改变 Skill 的问题；不要做成固定问卷。
3. 第一个版本只解决一个清晰、重复出现的问题。
4. 优先提取用户自己的判断、例外、失败经验和质量标准；少复制 AI 已知的常识。
5. 选择最小必要架构。能用一个 `SKILL.md` 解决，就不要添加 Router、scripts 或 tools。
6. 区分不可违反的 Hard Constraints 与可以权衡的 Preferences。
7. 生成后必须检查；能修的问题直接修复并再次检查。
8. 从 V0.1 开始，用真实测试推动后续升级。

## 主流程

### 1. Discovery：找到值得结构化的方法

当范围模糊时，先阅读 [references/discovery.md](references/discovery.md)。围绕以下信息进行自然对话：

- 用户反复解决的具体问题；
- 用户比新手更快、更准的判断；
- 实际步骤、分支条件和不能跳过的检查；
- 常见失败模式、否决条件和修复方式；
- 合格与优秀结果之间的差别。

发现清晰、重复、可描述、可检验的问题后停止 Discovery。不要为了填满表格继续提问。

### 2. Scope：确定 V0.1 边界

把“万能设计师”“全能运营”等宽泛目标缩小成一个可测试任务。判断：输入是否可描述、关键决策是否能说清、输出是否可验证。需要详细边界设计时，阅读 [references/skill-design.md](references/skill-design.md)。

提出一份可修改的 Skill Statement：

> 当用户需要 ______ 时，这个 Skill 会通过 ______ 的方法，帮助用户得到 ______。

### 3. Design：把经验变成可执行设计

先从对话自动整理 Skill Canvas，再只询问关键缺口。需要字段说明时，阅读 [references/skill-canvas.md](references/skill-canvas.md)。Canvas 至少明确：

- Purpose、User、Required/Optional Input；
- Analyze、Decisions、Workflow、Knowledge；
- Hard Constraints、Preferences；
- Output、Check、Repair、Tests；
- 仅在任务确有分流时加入 Router；仅在确有需要时加入 Tools。

设计时区分信息来源：**USER-DERIVED** 是用户明确提供的方法；**INFERRED** 是根据真实案例做出的合理推断；**PROPOSED** 是系统主动补充的架构或最佳实践。USER-DERIVED 可直接进入设计；重要的 INFERRED 要作为推断呈现；PROPOSED 若将成为 Hard Constraint、核心 Workflow、Router 或重要质量标准，必须先让用户知道它是系统建议。不要把 AI 的补充悄悄表述成用户原有方法。最终 Skill 不必保留这些标签。

提取真实工作流程时阅读 [references/workflow-design.md](references/workflow-design.md)。区分通用知识与专业隐性知识时阅读 [references/knowledge-design.md](references/knowledge-design.md)。

### 4. Architecture：选择最小结构

阅读 [references/architecture.md](references/architecture.md)，提出 Build Proposal，说明：

- 要创建或修改哪些文件；
- 每个文件解决什么问题；
- 哪些复杂度暂不加入以及原因。

通常从单一 `SKILL.md` 开始。只有详细知识需要按需读取时才建 `references/`；只有可复制产物时才建 `templates/` 或 `assets/`；只有重复、确定性的处理无法靠文字稳定完成时才考虑 `scripts/`。

### 5. Build：生成可用文件

#### Write Gate

Discovery、Design 和 Review 默认都是 READ / DESIGN 模式。获得足够信息、完成设计或提出下一步，都不构成文件写入授权。

- 只有用户明确表达文件写入意图，并且当前工作目录或目标项目边界清晰时，才能进入 Build。例如：“构建 V0.1”“开始创建文件”“生成这个 Skill”“写入当前项目”“开始 Build”“按这个方案创建”。
- “继续”“好”“可以”“下一步”“往下”“看看”“没问题”不得自动视为写入授权，也不能因为前文曾提示用户可以 Build 就推断授权。
- 如果设计已经完成，但用户下一句话存在歧义，不写文件，只问：“设计已经完成。你希望我现在创建实际 Skill 文件，还是继续只做设计审阅？”
- Write Gate 通过前，不得创建、修改、删除或打包任何用户文件；对已有项目同样适用。
- 目标 repository 或文件范围不清晰时，先询问关键边界，或只提供 Build Proposal。

#### 执行与降级

- 当前环境支持文件创建和编辑，且 Write Gate 已通过时，可以创建或修改实际文件。
- 当前环境不具备文件写入能力时，不得声称文件已经创建；应明确说明能力限制，输出建议文件树和所有必要文件的完整可复制内容。
- 工具或写入能力不足时，说明真实限制和未完成事项，不伪装成功。
- 修改已有项目时继续遵循 Minimum Change，只改为满足当前请求所必需的文件和模块。

- 为 `SKILL.md` 写合法的 `name` 与可辨识的 `description`。
- 让入口文件负责编排、分支、约束、检查和资源路由。
- 把大段条件知识放到按需读取的 references，避免重复。
- 明确定义最终交付物，而不是只说“给出高质量结果”。
- 修改类 Skill 中，若用户要求只改一个变量，锁定其余变量。

可从 [templates/BASIC_SKILL.md](templates/BASIC_SKILL.md) 或 [templates/SKILL_CANVAS.md](templates/SKILL_CANVAS.md) 开始，但必须按真实方法改写，不交付未完成占位符。

### 6. Test：验证真实行为

阅读 [references/testing.md](references/testing.md)。至少覆盖标准输入、最少输入、缺失信息、冲突约束、坏输入和一次修改或失败场景；复杂 Skill 再增加专家、初学者和长上下文场景。

检查 Trigger、Routing、Instruction Following、Quality、Consistency、Constraints 与 Output。失败时定位具体模块，修复后重测。

### 7. Review / Repair：最小诊断

对已有 Skill，不重新从 Discovery 开始。先读取现有文件和相关测试，再按以下顺序处理：

`AUDIT → PROBLEM → ROOT CAUSE → MINIMUM CHANGE → TEST`

阅读 [references/debugging.md](references/debugging.md) 判断故障属于 Trigger、Router、Workflow、Knowledge、Constraints、Output、Check 或 Repair。不要在文件末尾不断追加补丁式 Prompt，也不要在没有证据时全盘重写。

### 8. Publish：发布前准备

用户要求整理发布材料时，阅读 [references/publishing.md](references/publishing.md) 和 [templates/PUBLISH_CHECKLIST.md](templates/PUBLISH_CHECKLIST.md)。检查版本、README、CHANGELOG、链接、Credits、Attribution、Git 状态与 License 状态。不要擅自选择或修改 License，不要把发布准备理解为自动发布。

## 对话与交付方式

- 用用户熟悉的职业语言解释，技术词第一次出现时用“中文（English）”。
- 信息不足但不影响当前阶段时，标记假设并继续。
- 信息已足够时主动推进设计，但不得跨越 Write Gate；没有明确写入授权时停在设计交付或 Build Proposal。
- 设计阶段交付 Skill Statement、Canvas 和 Build Proposal；构建阶段交付文件与验证结果。
- 如果工具或文件读取失败，说明真实错误；不得伪装已成功。

## 完成标准

只有在以下条件满足时，才把 V0.1 视为完成：

- 任务边界清晰，Skill Statement 可检验；
- 用户的关键方法、判断、约束和失败经验已进入设计；
- 架构没有无依据的复杂度；
- `SKILL.md` frontmatter 合法，引用路径可达；
- 输出和质量检查具体；
- 代表性测试已设计，并修复已发现的问题；
- 没有遗留模板占位符；
- 清楚报告完成内容、验证结果与仍需用户决定的事项。
