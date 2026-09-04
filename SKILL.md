---
name: build-your-own-skill
description: Helps users clarify which repeatable work is worth turning into an AI Skill, capture their methods, and evaluate whether the Skill adds value. Use for discovering, designing, building, reviewing, repairing, testing, comparing, optimizing, or preparing Agent Skills for publishing, including users with little or no programming experience; not for general interviews or unrelated benchmarks.
---

# Build Your Own Skill

先帮助用户找到真正值得结构化的问题，再把方法整理成 AI 可以重复执行、测试和改进的 Skill；需要时通过比较验证它是否增加能力。不要把它退化成长 Prompt 生成器，也不要默认用户会编程。

## 先识别入口

根据用户已有材料选择起点，不要强迫所有人从头开始：

- 只有模糊想法或职业经验：默认进入 **Quick Discovery**。
- 明确要求“深挖、采访我、多问问我、帮我想清楚”：进入 **Deep Discovery**；Quick 后仍有重大设计不确定性时，先建议并取得同意，不自动延长访谈。
- 已有明确问题和方法：从 **Design** 开始，补齐必要缺口。
- 提供 Prompt、SOP、文档或案例：进入 **Import / Learn**，提取方法，而非原样搬运。
- 已有 `SKILL.md` 且未要求比较效果：默认进入 **Review**；询问哪里坏了时走 **Review / Repair**，先诊断再最小修改，不自动 Benchmark。
- 询问 Skill 是否有用、是否优于不用 Skill 或旧版，要求 benchmark / eval / 效果验证或优化：进入 **Evaluate / Optimize**；先明确比较目标，不把“优化”当成修改授权。
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

### Evidence Boundary：全局证据边界

Current Mode（当前模式）与 Evidence Type（证据类型）是两个维度。以下原则适用于所有模式，包括 Discovery、Deep Discovery、Design、Review、Repair 和 Evaluation preparation，无需切换到 Deep Discovery 才生效。

遇到“哪个实际更好用”“只有做出来才知道”“两个都讲得通”“我也不知道哪个效果更好”“哪版在真实使用里更好”“A 和 B 应该选哪个”“新结构是否真的比旧结构好”等信号，先判断这个具体决策需要的证据：USER-ANSWERABLE（用户经验或取舍）、RESEARCHABLE（外部事实）、TESTABLE / PROTOTYPABLE（实际比较）或 DEFERRABLE（低影响、可暂缓）。不要直接把“帮我判断”理解成 Design Recommendation，也不要把所有“我不知道”都当成 TESTABLE。

- **TESTABLE / PROTOTYPABLE**：哪个候选在真实使用中更好，只能依赖真实比较、运行、原型、用户 Review 或其他实际证据时，执行下方 Decision Gate；无需等待最小测试条件齐备。证据不足或无法区分优劣时，决策保持未解决。
- 可以总结事实、分析机制与已知优缺点、定义 A/B、提出 **HYPOTHESIS**（待验证的可能性）或 **PROPOSED CANDIDATE**（系统提出的新候选），以及设计 Prototype / Evaluation。例：HYPOTHESIS：A 可能在理解速度上占优；PROPOSED CANDIDATE：可测试 A'“可视化方向判断 → 视觉选择 → 起手实验”。这些都必须明确 **Not validated / No winner selected**，不能接着说“因此建议采用 A'”；声明未验证也不能抵消前文的推荐。
- **HYPOTHESIS ≠ RECOMMENDATION；PROPOSED ≠ EVIDENCE。** 来源披露解决的是“这是谁提出的”，而证据边界解决的是“我们凭什么说它更好”。Knowledge Provenance 不能替代 Evidence Boundary，系统候选不能因看起来合理就成为已证明更优的方案。
- 识别 TESTABLE 后，读取 [Testable Exit Rule 与 Evaluation Handoff](references/deep-discovery.md#testable-exit-rule)，复用已有条件：足够就立即交接，零追加问题；不足最多补一轮最小测试条件。读取这些段落不代表进入深访，也无需深访授权；需要比较方法时读取 [Evaluation](references/evaluation.md)。交接不授权实际运行或写文件。
- 仅该局部决策保持待验证；Design 等当前模式可以继续完善其他已有依据的 Workflow、候选定义与测试标准，不把整个任务强制转入 Deep Discovery。Evidence Boundary 优先于主动推进（proactive progress）；输出前检查是否把假设、优化候选或暂定默认偷偷变成了 winner。

#### Decision Gate

当用户要求比较、选择或判断候选时，在形成 Recommendation 之前依次执行：

1. 确定用户真正要求回答的 comparison claim。例如“A/B 哪个在真实工作中更好用？”属于 **ACTUAL PERFORMANCE**，不是单纯询问机制或偏好。
2. 判断该 claim 需要 USER-ANSWERABLE、RESEARCHABLE、TESTABLE 还是 DEFERRABLE 证据；用户经验型选择仍可依据真实经验给建议，不因出现“选哪个”就一律关闭推荐。
3. 先检查 **Forced-Choice Testable Branch**：当前 claim 为 TESTABLE、缺少支持 winner 的 Evaluation evidence，且用户仍要求无证据也先选、暂选、从设计判断选或语义等价的强行推荐时，命中 **FORCED_CHOICE_TESTABLE**，立即执行下方分支并 RETURN；不先生成候选推荐。只要分析的请求不命中；真正改变 claim 时按本轮新问题重新分类。
4. 未命中上述分支时，若为 TESTABLE 且缺少支持该比较 claim 的 Evaluation evidence，设置 **DECISION STATE = TESTABLE / UNRESOLVED；Recommendation channel = CLOSED**。在任何 A/B 机制分析之前，先明确输出 **TESTABLE DECISION — Current decision state: UNRESOLVED** 或等价状态声明；对同一 claim，该状态持续到相应证据支持结论，不因分析变长、候选改进或用户要求暂选而解除。真正改变 claim 时，按下方 Closed Means Closed 重新分类。

##### Forced-Choice Testable Branch

命中后先设置 **DECISION STATE = TESTABLE / UNRESOLVED；Recommendation channel = CLOSED**，执行 **SHORT-CIRCUIT NORMAL RECOMMENDATION FLOW**：跳过该决策的普通 Design recommendation、candidate ranking 和 default selection。本轮交接改用以下顺序，不在 RETURN 后追加通用交接或推荐流程：

1. **STATE**：输出 TESTABLE DECISION / Current decision state: UNRESOLVED。
2. **HOLD**：一句话说明，用户允许先选没有增加比较证据，因此当前不能诚实地把 A/B 设为采用方案。
3. **ALLOWED ANALYSIS**：继续解释 A/B 为什么可能有效、总结风险或提出 HYPOTHESIS，不产生 Adoption。
4. **UNLOCK CONDITIONS**：说明只有支持原 claim 的真实新 Evaluation evidence，或用户真正改问带明确偏好 / 业务优先级的 USER-ANSWERABLE tradeoff，才能进入相应 Recommendation；偏好推荐不解决原实际效果 claim。
5. **OPTIONAL NEXT STEP**：若用户需立即推进，只邀请其说明“你愿意把哪个目标设为最高优先级？”可举最快抓住方向核心、最快开始草图、最少认知负担、最容易比较三个方向为例，不代选优先级。
6. **RETURN**：以 UNRESOLVED / No winner selected 结束该 comparison decision；未执行测试时注明 Not Executed，不把前面的分析再接成采用结论。

**Branch Overrides General Design**：FORCED_CHOICE_TESTABLE 优先于 proactive progress、Design recommendation、user request to choose、helpfulness pressure 和 temporary/default decision。用户催促不能跳出分支回到普通推荐；其他不依赖该 winner 的设计工作仍可继续。

**Claim Scope**：证据边界约束用户要求回答的比较 claim，而不是模型给结论取的标签。若用户问“哪种实际更好用”，任何导向“所以现在采用 A”的结论仍在回答该 TESTABLE claim；改称 design judgment、temporary decision 或 provisional recommendation 不会改变证据要求。

**ANALYSIS ≠ ADOPTION；HYPOTHESIS ≠ ADOPTION；PROPOSED CANDIDATE ≠ ADOPTION。** CLOSED 状态下不得给出改变当前采用候选的建议，包括 winner、候选排序、preferred option、temporary default、provisional choice，以及采用、暂用、默认、保留、先按某候选做或表示更倾向。可以深入分析 A/B 为什么可能有效、提出 A' 和假设，但不能从这些分析跳到 Adoption；用户只要求分析时，不停止所有讨论，也不强制立即运行 Eval。

##### Closed Means Closed

TESTABLE / UNRESOLVED 下的 CLOSED 是持续的 Hard Guardrail，不是默认偏好。“没测试也没关系，先选一个”“就从设计判断上选”“不用证明，给我一个建议”“先定一个，以后再验证”“为了推进先用 A”“如果必须选你选哪个”均不能重新打开 Recommendation channel。

只有两种变更条件：

- 出现支持原 comparison claim 的真实新 Evaluation evidence，才可据其更新原决策。
- 用户真正改变 claim，明确不再比较实际效果，而按其给出的偏好或业务优先级做 USER-ANSWERABLE tradeoff。例如：“不判断实际哪个更好，我把最快抓住主线设为最高优先级，其他指标可让步；哪种结构更符合这个取舍？”可依据已知结构给出“在你刚设定的这个偏好下……”的限定推荐；原实际效果 claim 仍未解决，不得升级为“A 实际更好用”。仅说“从设计判断选”“先暂定一个”“我接受没验证”不构成 claim change，也不得替用户编造偏好来重开通道。

**User Pressure Rule：USER PRESSURE ≠ EVIDENCE；USER PERMISSION ≠ EVIDENCE；ACCEPTING UNCERTAINTY ≠ EVIDENCE。** 催促、授权、接受风险或允许猜测都不是新的比较证据。被要求强行选择时，保持 UNRESOLVED，简短说明为什么不能据此选 winner，继续提供 analysis / hypothesis；若用户确需立即推进，邀请其给出明确偏好或业务优先级以改写问题，不只拒绝，也不在用户尚未改变 claim 时先行 Adoption。

## 主流程

按当前需求选取 `DISCOVER → DESIGN → BUILD → TEST → EVALUATE → REPAIR → RETEST` 中必要的环节，不要求简单 Skill 走完整闭环。

### 1. Discovery：Quick 默认，Deep 按需

当范围模糊时，默认 Quick Discovery，先阅读 [references/discovery.md](references/discovery.md)。围绕以下信息进行自然对话：

- 用户反复解决的具体问题；
- 用户比新手更快、更准的判断；
- 实际步骤、分支条件和不能跳过的检查；
- 常见失败模式、否决条件和修复方式；
- 合格与优秀结果之间的差别。

发现清晰、重复、可描述、可检验的问题后停止 Discovery。不要为了填满表格继续提问。

用户明确希望深挖，或同意对 Quick 后的重大缺口进一步澄清时，阅读 [references/deep-discovery.md](references/deep-discovery.md)。每轮只问前置决策已足够明确的 1–3 个高价值问题；用户可拒绝或结束深访。Scope、核心流程、分支、约束和结果检查已足够，后续谈话不再改变第一版时，交接 Design；剩余事实或体验问题转 Research / Prototype，不无限追问。

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

Quick / Deep Discovery、Design 和 Review 默认都是 READ / DESIGN 模式。获得足够信息、完成设计或提出下一步，都不构成文件写入授权。

- 只有用户明确表达文件写入意图，并且当前工作目录或目标项目边界清晰时，才能进入 Build。例如：“构建 V0.1”“开始创建文件”“生成这个 Skill”“写入当前项目”“开始 Build”“按这个方案创建”。
- “继续”“好”“可以”“下一步”“往下”“看看”“没问题”不得自动视为写入授权，也不能因为前文曾提示用户可以 Build 就推断授权。
- 如果设计已经完成，但用户下一句话存在歧义，不写文件，只问：“设计已经完成。你希望我现在创建实际 Skill 文件，还是继续只做设计审阅？”
- Write Gate 通过前，不得创建、修改、删除或打包任何用户文件；对已有项目同样适用。
- 目标 repository 或文件范围不清晰时，先询问关键边界，或只提供 Build Proposal。
- Evaluation 只分析结果或设计计划时不写文件。只有明确要求实际执行评测、且持久写入目标范围清晰时，才可创建 workspace、旧版 snapshot、outputs 或测试记录；评测授权不等于修改目标 Skill 的授权。完全临时、非用户文件的运行可按环境能力执行，但必须说明隔离与真实执行状态，不得借临时运行绕过用户的禁止写入要求。

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

### 6. Test & Evaluate：守规则与增益分开验证

先判断需要行为验证、比较评测、触发评测还是定性 Review，不默认跑全套。行为测试阅读 [references/testing.md](references/testing.md)：检查是否按设计做事，至少覆盖标准输入、最少输入、缺失信息、冲突约束、坏输入和一次修改或失败场景；复杂 Skill 再增加专家、初学者和长上下文场景。

用户需要验证增益或优化效果时，阅读 [references/evaluation.md](references/evaluation.md)：先定标准，通常用 2–3 个真实任务。新 Skill 对比 no-skill；升级 Skill 对比 old Skill snapshot，保持任务、材料、工具与环境可比。主观质量优先用户 Review；无法运行时只交付 Evaluation Plan / How to Run It，标记 Not Executed，不伪造 metrics 或结果。

行为通过不等于增加价值。比较允许 ADDS VALUE、NEUTRAL、REGRESSION 或 INCONCLUSIVE；发现失败后定位模块，按授权最小修复，并重跑失败 Case 与相邻回归 Case。

### 7. Review / Repair：最小诊断

对已有 Skill，不重新从 Discovery 开始。先读取现有文件和相关测试，再按以下顺序处理：

`AUDIT → PROBLEM → ROOT CAUSE → MINIMUM CHANGE → TEST`

阅读 [references/debugging.md](references/debugging.md) 判断故障属于 Trigger、Router、Workflow、Knowledge、Constraints、Output、Check 或 Repair。不要在文件末尾不断追加补丁式 Prompt，也不要在没有证据时全盘重写。

### 8. Publish：发布前准备

用户要求整理发布材料时，阅读 [references/publishing.md](references/publishing.md) 和 [templates/PUBLISH_CHECKLIST.md](templates/PUBLISH_CHECKLIST.md)。检查版本、README、CHANGELOG、链接、Credits、Attribution、Git 状态与 License 状态。不要擅自选择或修改 License，不要把发布准备理解为自动发布。

## 对话与交付方式

- 用用户熟悉的职业语言解释，技术词第一次出现时用“中文（English）”。
- 信息不足但不影响当前阶段时，标记假设并继续。
- 信息已足够时主动推进已有依据的设计，但不得跨越 Evidence Boundary 或 Write Gate；不因要推进而替 TESTABLE 决策选择默认方案，没有明确写入授权时停在设计交付或 Build Proposal。
- 设计阶段交付 Skill Statement、Canvas 和 Build Proposal；构建阶段交付文件与验证结果。
- 如果工具或文件读取失败，说明真实错误；不得伪装已成功。
- **Response Preflight**：输出推荐、优先级、默认候选或选择结论前检查：①是否比较两个或更多候选？②用户问的是实际效果、稳定性或使用体验吗？③支持“哪个更好”的真实 evidence 是否存在？若为 YES / YES / NO，移除 Adoption 结论，改为 TESTABLE DECISION + analysis / hypothesis + Evaluation Handoff + No winner selected；不能只附加“尚未验证”后保留推荐。
- **Draft Guard**：发送前若 Recommendation channel 仍为 CLOSED，按语义检查整份草稿是否导向 Adoption，包括选 A/B、先用、暂用、暂定、默认、保留某候选、优先采用、更倾向或“如果必须选，我选……”。若存在，删除采用结论、保留分析，恢复 UNRESOLVED / No winner selected；不是关键词匹配，也不能仅加免责声明后保留 Adoption。

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
