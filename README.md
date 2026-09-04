# Build Your Own Skill

## 把你的经验，变成 AI 可以执行的能力

Build Your Own Skill 是一个帮助你从 0 制作自己 AI Skill 的 Skill。

你不需要先会编程。告诉它你擅长什么、平时怎么工作、想重复解决什么问题，它会陪你把经验逐步整理成：

`你的经验 → 隐性知识 → Skill Canvas → Workflow → SKILL.md → Tests → V0.1`

> 不要只教 AI 一句话。把你解决问题的方法，教给它。

当前版本是 **V0.2.0**：第一版经过实机测试与关键安全修复的 Skill Builder。

## 它和 Prompt Generator 有什么不同？

Prompt 常常解决一次任务。Workflow 解决一类任务。Skill 则把触发条件、工作步骤、专业判断、约束、交付格式和质量检查组合成一套可以重复执行、测试和改进的能力。

Build Your Own Skill 不会在你说“我想做一个 Skill”后立刻吐出一份很长的 `SKILL.md`。它会先帮助你发现：

- 你反复解决的具体问题是什么；
- 你有哪些新手不容易看到的判断；
- 什么情况会让你改变做法；
- 哪些错误绝对不能发生；
- 怎样的结果才算合格或优秀。

真正有价值的通常不是 AI 本来就知道的百科知识，而是你在实践中形成的方法。

## 谁适合使用？

设计师、摄影师、导演、艺术家、创作者、文案、运营、产品经理、品牌从业者、HR、顾问、教师、研究者、程序员，以及任何拥有可复用经验的人。

完全不会代码也可以。你只需要用自然语言描述真实工作；YAML、工作流结构和测试设计由 Skill 帮你整理。

如果你已经熟悉 Agent Skills，也可以直接提供现有 Prompt、SOP、`SKILL.md` 或架构要求，它会跳过不必要的新手步骤。

## 如何开始

从一句自然语言开始即可：

> 我是摄影师，我想把自己的餐厅摄影方法做成一个 Skill。

> 我经常帮别人做品牌视觉提案，我想把流程固定下来。

> 这是我现在的 SKILL.md，帮我检查为什么结果不稳定。

> 我有一套自己的小红书选题方法，怎么做成 Skill？

> 我完全不会代码，也能做吗？

如果想直接尝试，可把本仓库作为 Skill 提供给支持 Agent Skills 的 AI，然后描述你的想法或附上现有材料。核心入口是 [`SKILL.md`](SKILL.md)。

Build Your Own Skill 可以在支持文件操作的 Agent 中直接构建；在纯对话环境中则会输出完整的 Skill 设计和可复制文件内容。

## 从和你最像的情况开始

| 你现在的起点 | 推荐案例 |
| --- | --- |
| 我只有自己的工作经验 | [Case 01：Experience → Skill](case-studies/01-experience-to-skill/) |
| 我已经有一条很长的 Prompt | [Case 02：Prompt → Skill](case-studies/02-prompt-to-skill/) |
| 我已经有一个 Skill，但不好用 | [Case 03：Review → Repair](case-studies/03-review-and-repair/) |

这三个案例均来自 Build Your Own Skill 的真实实机测试，不是为了教程临时编造的虚拟 Persona。

## 你会经历什么

1. **Discovery**：从真实案例发现重复问题和隐性知识，而不是填写长问卷。
2. **Scope**：把“万能助手”缩小成一个清晰、可测试的 V0.1。
3. **Skill Statement**：用一句话确认触发场景、方法和结果。
4. **Skill Canvas**：自动整理用户、输入、判断、流程、约束、输出和测试。
5. **Workflow & Knowledge**：提取你真实的步骤、分支、失败经验和质量标准。
6. **Architecture**：只选择当前真正需要的文件和工具。
7. **Build**：生成可用的 `SKILL.md` 与必要支持文件。
8. **Test & Repair**：用正常、缺失、冲突和失败场景验证，再针对根因修复。
9. **V0.1**：得到可以继续真实使用和升级的第一版。

系统会尽量从已有对话推断信息，每轮只问少量会实质改变结果的问题；信息足够后主动推进，不要求你把 Canvas 当申请表填写。

## 你可以得到什么

根据任务复杂度，交付可能包括：

- 一份明确的 Skill Statement；
- 一张已从对话整理的 Skill Canvas；
- 用户真实方法对应的 Workflow；
- Hard Constraints、Preferences、Check 与 Repair；
- 可直接使用的 `SKILL.md`；
- 必要的 references 或 templates；
- 代表性测试与 V0.1 改进建议。

简单 Skill 可能只需要一个文件。只有真实需求证明有必要时，才增加 Router、scripts、tools 或更多目录。

## 项目结构

```text
build-your-own-skill/
├── SKILL.md
├── README.md
├── CHANGELOG.md
├── AGENTS.md
├── references/
│   ├── discovery.md
│   ├── skill-design.md
│   ├── skill-canvas.md
│   ├── workflow-design.md
│   ├── knowledge-design.md
│   ├── architecture.md
│   ├── testing.md
│   ├── debugging.md
│   └── publishing.md
├── templates/
│   ├── SKILL_CANVAS.md
│   ├── BASIC_SKILL.md
│   └── PUBLISH_CHECKLIST.md
├── examples/
│   └── brand-visual-director/
│       ├── SKILL.md
│       └── README.md
├── case-studies/
│   ├── README.md
│   ├── 01-experience-to-skill/
│   ├── 02-prompt-to-skill/
│   └── 03-review-and-repair/
└── tests/
    └── cases.md
```

- `SKILL.md` 是精简的编排层，识别用户阶段并决定何时读取详细资料。
- `references/` 保存 Discovery、设计、架构、测试和诊断方法。
- `templates/` 提供可以复制并按真实经验改写的起点。
- `examples/` 展示最终 Skill 的结构示例。
- `case-studies/` 展示真实用户从起点到发现、设计、构建或修复 Skill 的过程。
- `tests/` 描述 Skill 自身应通过的行为场景。

## 推荐阅读

- 不知道该做什么：[`references/discovery.md`](references/discovery.md)
- 已有明确想法：[`references/skill-design.md`](references/skill-design.md)
- 想整理完整设计：[`templates/SKILL_CANVAS.md`](templates/SKILL_CANVAS.md)
- 想从最小文件开始：[`templates/BASIC_SKILL.md`](templates/BASIC_SKILL.md)
- Skill 表现不稳定：[`references/debugging.md`](references/debugging.md)
- 想看完整例子：[`examples/brand-visual-director/`](examples/brand-visual-director/)
- 想看真实制作过程：[`case-studies/`](case-studies/)
- 只有经验：[Case 01：Experience → Skill](case-studies/01-experience-to-skill/)
- 已有长 Prompt：[Case 02：Prompt → Skill](case-studies/02-prompt-to-skill/)
- 已有 Skill 想修：[Case 03：Review → Repair](case-studies/03-review-and-repair/)

## 设计原则

- Infer whenever reasonable：能从上下文推断，就不重复问。
- 一次只追问 1–3 个真正重要的问题。
- Complexity must solve a real problem：复杂度必须解决真实问题。
- Generate → Check → Repair → Recheck。
- 不断追加 Prompt 不是调试；先定位 Trigger、Workflow、Knowledge、Constraint 或 Output。
- 从 V0.1 开始，不在第一天假装已经是 V1.0。

## 开源与二次创作

我们鼓励真正的学习与扩展：

`STUDY → UNDERSTAND → MODIFY → EXTEND → CREDIT → SHARE`

基于其他项目创建 Skill 时，请查看原项目 License，保留必要 Attribution，说明来源和修改，并遵守原 License。不要把改名字、换 Logo 当成真正的二次创作。

## License

本仓库当前尚未设置 License，需要项目作者决定。缺少 License 不等于自动获得任意复制、修改或再发布许可。
