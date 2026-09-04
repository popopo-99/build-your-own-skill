# Build Your Own Skill

## 把你的经验，变成 AI 可以执行的能力

Build Your Own Skill 是一个帮助你从 0 制作自己 AI Skill 的 Skill。

> Agent Skill 是一组让 AI 在特定任务中重复遵循的方法、判断规则和质量检查。

Build Your Own Skill 会把你的经验、Prompt、SOP 或现有 Skill，逐步整理成 AI 可以重复执行的方法：

`你的经验 / Prompt / SOP → 找出真正的方法和判断 → 整理成可执行流程 → 做成 Skill → 测试和改进`

你不需要先会编程。只需要告诉它你擅长什么、平时怎么工作，或者直接提供已有材料。

> 不要只教 AI 一句话。把你解决问题的方法，教给它。

## 它和 Prompt Generator 有什么不同？

Prompt 常常解决一次任务。Workflow 解决一类任务。Skill 则把触发条件、工作步骤、专业判断、约束、交付格式和质量检查组合成一套可以重复执行、测试和改进的能力。

Build Your Own Skill 不会在你说“我想做一个 Skill”后立刻吐出一份很长的 `SKILL.md`。它会先帮助你发现：

- 你反复解决的具体问题是什么；
- 你有哪些新手不容易看到的判断；
- 什么情况会让你改变做法；
- 哪些错误绝对不能发生；
- 怎样的结果才算合格或优秀。

真正有价值的通常不是 AI 本来就知道的百科知识，而是你在实践中形成的方法。

## 原来这些经验都可以做成 Skill

Skill 不只属于程序员或 AIGC 创作者。只要一项工作反复发生，而且你已经会判断例外、风险和取舍，就可能值得整理：

| 职业起点 | 原本的问题 → 最后提取出的 Skill |
| --- | --- |
| 视觉设计师 | 不知道什么值得做 → [从模糊活动 Brief 中提取“活动创意方向推导”](case-studies/04-visual-designer-discovery/) |
| AIGC 短剧导演 | 会拆镜但说不清方法 → [把导演判断整理成可制作镜头拆解规则](case-studies/05-aigc-director-experience/) |
| 咖啡店店长 | 每天凭经验备货排班 → [把异常、补救成本与岗位瓶颈变成判断流程](case-studies/06-cafe-manager-experience/) |

这些是基于真实运行过程整理的教学案例；场景材料经过匿名化、改写或复合设计。它们展示如何提取方法，不是职业效果验证报告。

## 3 分钟安装并开始

### 1. 在 Codex 中安装

在 Codex 中调用 `$skill-installer`，并给它下面这段自然语言安装请求：

```text
$skill-installer

Install the skill from:
https://github.com/popopo-99/build-your-own-skill
```

推荐安装完整 Skill 目录，而不是只下载 `SKILL.md`；Build Your Own Skill 还会使用 references、templates 和 tests 等支持内容。

详细安装、手动安装和排错见 [`INSTALL.md`](INSTALL.md)。

### 2. 确认安装成功

在 Codex CLI 或 IDE 中输入 `$`，或使用 `/skills`，查找 `build-your-own-skill`。如果刚安装后没有出现，再尝试重启 Codex。

### 3. 复制第一句话

```text
$build-your-own-skill

我想把自己的一套工作方法做成一个 Skill。
先帮我做 Discovery，不要创建或修改任何文件。
```

如果你已经有 Prompt 或 `SKILL.md`，也可以直接粘贴，不需要从零开始。

> Build Your Own Skill 默认可以先只做分析和设计。只有当你明确要求 Build / 创建文件时，才应进入文件写入阶段。

## 从和你最像的情况开始

| 你现在的起点 | 推荐案例 | 你可以这样开始 |
| --- | --- | --- |
| 我只有自己的工作经验 | [Case 01：Experience → Skill](case-studies/01-experience-to-skill/) | 描述一次你真实做过的工作 |
| 我已经有一条很长的 Prompt | [Case 02：Prompt → Skill](case-studies/02-prompt-to-skill/) | 直接粘贴 Prompt，让它先分析 |
| 我已经有一个 Skill，但不好用 | [Case 03：Review → Repair](case-studies/03-review-and-repair/) | 提供 `SKILL.md` 和具体失败表现 |

> 不需要提前整理成标准格式。真实案例、旧 Prompt、SOP 或现有 Skill 都可以直接作为起点。

上表 Case 01–03 均来自 Build Your Own Skill 的真实实机测试，不是为了教程临时拼出的流程。另有三个跨行业教程采用真实 Runtime 交互过程，并对职业场景和细节做了匿名化、改写或教学化处理；两组案例的定位见 [`case-studies/`](case-studies/)。

## 安装后，第一句话怎么说

### 从经验开始

```text
$build-your-own-skill

我经常负责 ______。
我有自己的一些判断方法，但从来没有系统整理过。
先帮我判断什么值得做成 Skill，不要创建文件。
```

### 从长 Prompt 开始

```text
$build-your-own-skill

这是我长期使用的一条 Prompt。
它效果不错，但越来越长、越来越难维护。
先帮我分析哪些内容应该变成 Workflow、Rules 和 References，
不要创建文件。

[粘贴 Prompt]
```

### 从已有 Skill 开始

```text
$build-your-own-skill

这是我现在的 SKILL.md，但它在实际使用中有一些问题。
先帮我定位根因和最小修改方案，不要直接重写或修改文件。

[粘贴 SKILL.md]
```

### 当你自己也不知道需求是什么

可以说：“多问我，帮我把这个 Skill 真正想清楚。”它会进入 [Deep Discovery（深度发现）](references/deep-discovery.md)，逐步澄清会改变设计的关键决策；普通请求仍默认 Quick Discovery，每轮只问 1–3 个问题。

### Skill 做完后，怎么知道它真的有用？

可以说：“帮我验证这个 Skill 是否真的减少返工。”通过 [Comparative Evaluation（比较评测）](references/evaluation.md)，用相同真实任务比较 With Skill 与 Without Skill；升级时比较新版与旧版。通常从 2–3 个任务开始，无法实际运行会明确说明，不把计划当成结果。

## 谁适合使用？

设计师、摄影师、导演、艺术家、创作者、文案、运营、产品经理、品牌从业者、HR、顾问、教师、研究者、程序员，以及任何拥有可复用经验的人。

完全不会代码也可以。你只需要用自然语言描述真实工作；YAML、工作流结构和测试设计由 Skill 帮你整理。

如果你已经熟悉 Agent Skills，也可以直接提供现有 Prompt、SOP、`SKILL.md` 或架构要求，它会跳过不必要的新手步骤。

## 你会经历什么

1. **Discovery**：从真实案例发现重复问题和隐性知识，而不是填写长问卷。
2. **Scope**：把“万能助手”缩小成一个清晰、可测试的 V0.1。
3. **Skill Statement**：用一句话确认触发场景、方法和结果。
4. **Skill Canvas**：自动整理用户、输入、判断、流程、约束、输出和测试。
5. **Workflow & Knowledge**：提取你真实的步骤、分支、失败经验和质量标准。
6. **Architecture**：只选择当前真正需要的文件和工具。
7. **Build**：生成可用的 `SKILL.md` 与必要支持文件。
8. **Test / Evaluate / Repair**：先验证行为；需要判断增益时再比较结果，针对根因修复并重测，不强制完整 Benchmark。
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
├── INSTALL.md
├── CHANGELOG.md
├── LICENSE
├── COMMONS-CLAUSE.md
├── NOTICE
├── AGENTS.md
├── references/
│   ├── discovery.md
│   ├── deep-discovery.md
│   ├── skill-design.md
│   ├── skill-canvas.md
│   ├── workflow-design.md
│   ├── knowledge-design.md
│   ├── architecture.md
│   ├── testing.md
│   ├── evaluation.md
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
│   ├── 03-review-and-repair/
│   ├── 04-visual-designer-discovery/
│   ├── 05-aigc-director-experience/
│   └── 06-cafe-manager-experience/
└── tests/
    └── cases.md
```

- `SKILL.md` 是精简的编排层，识别用户阶段并决定何时读取详细资料。
- `references/` 保存 Quick / Deep Discovery、设计、架构、行为测试、效果评测和诊断方法。
- `templates/` 提供可以复制并按真实经验改写的起点。
- `examples/` 展示最终 Skill 的结构示例。
- `case-studies/` 展示经过说明的实机测试与教学演示，重点是从起点到发现、设计、构建或修复 Skill 的方法提取过程。
- `tests/` 描述 Skill 自身应通过的行为场景。

## 推荐阅读

- 不知道该做什么：[`references/discovery.md`](references/discovery.md)
- 已有明确想法：[`references/skill-design.md`](references/skill-design.md)
- 想整理完整设计：[`templates/SKILL_CANVAS.md`](templates/SKILL_CANVAS.md)
- 想从最小文件开始：[`templates/BASIC_SKILL.md`](templates/BASIC_SKILL.md)
- Skill 表现不稳定：[`references/debugging.md`](references/debugging.md)
- 想看真实制作过程：[`case-studies/`](case-studies/)

## 设计原则

- Infer whenever reasonable：能从上下文推断，就不重复问。
- 一次只追问 1–3 个真正重要的问题。
- Complexity must solve a real problem：复杂度必须解决真实问题。
- Generate → Check → Repair → Recheck。
- 不断追加 Prompt 不是调试；先定位 Trigger、Workflow、Knowledge、Constraint 或 Output。
- 从 V0.1 开始，不在第一天假装已经是 V1.0。

## 公开源码与二次创作

我们鼓励真正的学习与扩展：

`STUDY → UNDERSTAND → MODIFY → EXTEND → CREDIT → SHARE`

基于其他项目创建 Skill 时，请查看原项目 License，保留必要 Attribution，说明来源和修改，并遵守原 License。不要把改名字、换 Logo 当成真正的二次创作。

## Inspirations / References

V0.3 的 Deep Discovery 与 Evaluation 设计参考了以下工作的部分思想：

- [Anthropic — Skill Creator](https://github.com/anthropics/claude-plugins-official/blob/main/plugins/skill-creator/skills/skill-creator/SKILL.md)：意图提取、基线比较与反馈迭代。
- Matt Pocock — [grill-me](https://www.aihero.dev/skills-grill-me) / [grilling](https://github.com/mattpocock/skills/blob/main/docs/productivity/grilling.md)：按前置决策推进追问，以及识别需要研究或原型而非继续谈话的问题。

Build Your Own Skill 是独立实现，未将第三方 Skill 作为运行时依赖，也未复制其专属工具链。这些来源是设计启发，不代表联合开发。

## Version

当前版本：**V0.3.0**

V0.3.0 带来更深入的经验发现（Deep Discovery）、重视证据的比较评测（Comparative Evaluation）与跨行业教学案例：先搞清楚值得做什么，再验证 Skill 是否真正增加能力。

版本记录见 [`CHANGELOG.md`](CHANGELOG.md)。

## License

Build Your Own Skill is licensed under:

**Apache License 2.0 with the Commons Clause License Condition v1.0.**

正式文本见 [LICENSE](LICENSE)、[COMMONS-CLAUSE.md](COMMONS-CLAUSE.md)，项目来源信息见 [NOTICE](NOTICE)。这是公开源码、可学习和扩展的 **source-available** 项目；加入 Commons Clause 后，不属于 OSI 定义的开源软件。

### 你可以做什么

在遵守上述许可的前提下，你可以免费学习、使用、修改、Fork 本项目，分享合规的二次创作，也可以在公司内部或个人、商业工作中使用它。

例如：咖啡店用它整理运营方法，导演用它梳理商业短剧流程，设计师或顾问用它服务客户；你也可以基于自己的专业经验制作独立 Skill，并使用它承接商业项目。

### 使用工具创造自己的内容

使用本工具创建出的独立 Skill，不会仅因为使用了 Build Your Own Skill 就自动成为本项目的衍生版本。

如果你没有复制、修改或重新分发本项目本身的受保护内容，而是在整理自己的经验、SOP、Workflow 或专业内容，通常不要求在最终 Skill 或作品中写“Created by ZY”或“Based on Build Your Own Skill”。本项目许可不会仅因使用工具就要求你转让独立内容的权利；你仍需遵守所用其他材料的权利与许可。

你可以出售由自己专业经验形成的独立 Skill，前提是它不是在重新出售本工具，也不是下述价值全部或实质上来自本工具功能的产品或服务。

### 需要保留来源的情况

如果你 Fork、修改并重新发布 Build Your Own Skill，或复制其 `SKILL.md`、references、templates 等受保护内容形成衍生版，包括在此基础上继续开发另一个 Skill Builder，应按正式许可：

- 随再分发提供适用的 Apache License 与 Commons Clause 条件文本；
- 保留适用的版权和来源声明，以及 NOTICE 中的原项目名称、作者和仓库链接；NOTICE 的适用声明可按 Apache 2.0 第 4(d) 条保留在 NOTICE 文件、随附源码或文档等允许的位置；
- 在修改过的文件中清楚标明修改，不把衍生版冒充为原作者官方版本；
- 同时遵守 Commons Clause 的销售限制。

这里涉及的是对本项目受保护内容的复制、修改与再分发，不是把通用方法、想法或独立经验一概视为本项目的专有内容。

### 商业边界

可以“用这个工具开展商业工作”；限制的是“把这个工具本身拿去卖”，以及向第三方收取费用或其他对价，提供价值全部或实质上来自本工具功能的产品或服务。

仅改名、换 Logo、少量 Prompt 改写或轻微包装，再作为收费 Skill Builder 出售，不能绕过该限制。它也涉及符合上述价值来源条件的托管服务，以及与本工具相关的收费咨询或支持服务；并非禁止所有商业使用或所有咨询服务。

以上是便于理解的说明，不是新增许可证条款。最终授权以 [LICENSE](LICENSE) 和 [COMMONS-CLAUSE.md](COMMONS-CLAUSE.md) 为准，并按许可保留 [NOTICE](NOTICE) 中的适用来源信息；NOTICE 仅用于信息与署名说明，不修改许可，README 也不覆盖正式法律文本。
