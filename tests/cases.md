# Build Your Own Skill — Behavioral Test Cases

这些测试关注可观察行为，不要求逐字匹配固定回答。每次修改核心 Trigger、流程、约束或输出后，至少重跑受影响案例和一个相邻正常案例。

## Case 01 — 模糊的摄影师想法

**Input**

> 我是摄影师，我想做自己的 Skill。

**Expected behavior**

- 进入 Discovery，不立即生成 `SKILL.md`。
- 承认“摄影”范围过宽，询问 1–3 个关于重复任务、真实案例或专业判断的问题。
- 使用普通职业语言，不要求用户理解 YAML、Router 或 Shell。

**Failure signals**

- 直接输出通用摄影 Skill；
- 一次列出十几个 Canvas 字段要求填写。

## Case 02 — 万能设计 Skill

**Input**

> 帮我做一个万能设计 Skill。

**Expected behavior**

- 识别 Scope 过宽。
- 根据用户常做的问题提出少量候选边界，例如品牌视觉方向、设计 Review 或 KV 创意方向。
- 先确认一个可测试的 V0.1 问题。

**Failure signals**

- 接受“万能”目标并堆叠大量模式、工具和目录。

## Case 03 — Review 现有 Skill

**Input**

> 我已经有 SKILL.md，帮我看看为什么不好用。

**Expected behavior**

- 请求或读取现有 `SKILL.md` 与一个失败案例。
- 进入 `AUDIT → PROBLEM → ROOT CAUSE → MINIMUM CHANGE → TEST`。
- 优先定位 Trigger、Workflow、Knowledge、Constraints、Output、Check 或 Repair。

**Failure signals**

- 从职业访谈重新开始；
- 未读取原文件就全盘重写。

## Case 04 — 完全不会代码

**Input**

> 我完全不会代码，也能做吗？我是一名招聘顾问。

**Expected behavior**

- 明确可以继续，并用招聘工作的自然语言开始 Discovery。
- 询问重复处理的招聘问题或最近案例。
- 技术结构由系统内部处理。

**Failure signals**

- 要求先安装 Python、使用终端或编写 frontmatter。

## Case 05 — 很小的标题修改 Skill

**Input**

> 我想做一个 Skill，只帮我修改文案中的标题，正文一字不动。

**Expected behavior**

- 接受小范围，并应用 One Variable Rule：标题可变，正文、事实和结构锁定。
- 选择单一 `SKILL.md` 或更小方案，不默认增加 Router、references 或 scripts。
- 定义如何检查正文未变化。

**Failure signals**

- 同时润色正文；
- 为简单任务创建复杂多层架构。

## Case 06 — 信息已经完整

**Input**

> 我帮助独立餐厅把菜品表、场地照片和宣传目标变成拍摄顺序与镜头清单。我先按融化、氧化和塌陷速度排序，再结合出餐节奏；绝不为了画面好看承诺现场做不到的布景。输出要有准备、顺序、镜头、风险和备选方案。

**Expected behavior**

- 不继续大量追问。
- 自动整理 Skill Statement 与初步 Canvas。
- 标出少量合理假设，并提出最小架构建议。

**Failure signals**

- 再逐项询问 User、Input、Workflow 和 Output。

## Case 07 — 只有一句“帮我做”

**Input**

> 帮我做个 Skill。

**Expected behavior**

- 进入 Discovery。
- 只问 1–3 个高价值问题，例如经常重复完成什么、别人为何来找他、最近一次真实案例。
- 不把用户拖进技术术语。

**Failure signals**

- 直接交付模板；
- 显示 Question 1/20 一类固定问卷。

## Case 08 — 导入 SOP

**Input**

> 这是我的客户投诉处理 SOP，请把它做成 Skill。

**Expected behavior**

- 读取 SOP，提取输入、步骤、分支、升级条件、话术边界与完成标准。
- 区分固定制度与用户的专业判断。
- 只询问 SOP 中会影响安全或路由的关键缺口。

**Failure signals**

- 把 SOP 原样包在 `SKILL.md` 中；
- 忽略例外、升级和检查条件。

## Case 09 — 导入旧 Prompt

**Input**

> 我有一条很长的品牌提案 Prompt，想做成 Skill。

**Expected behavior**

- 分析 Prompt 中可复用的 Trigger、Workflow、Knowledge、Constraints 和 Output。
- 识别重复、冲突与泛化内容。
- 依据职责重组，而非原样搬运或继续追加 Prompt。

**Failure signals**

- 只加 YAML frontmatter 就称为 Skill；
- 未验证 Prompt 中的规则是否来自真实方法。

## Case 10 — 明显需要代码

**Input**

> 我每周要读取 50 个 CSV，统一列名、去重并生成错误报告，想做成 Skill。

**Expected behavior**

- 识别重复、确定性文件处理适合 scripts / tools。
- 先明确输入格式、去重键、异常处理和输出，再提出脚本结构。
- 解释为什么此处复杂度解决真实问题，并设计脚本失败测试。

**Failure signals**

- 仅用文字让模型手工处理大量文件；
- 在规则不清楚前先写脚本。

## Case 11 — 冲突约束

**Input**

> 保持原文每个字不变，同时把标题改得更短。

**Expected behavior**

- 识别“每个字不变”和“修改标题”冲突。
- 不伪装两者可以同时满足。
- 只请求用户决定哪个 Hard Constraint 优先。

**Failure signals**

- 私自选择优先级；
- 修改后声称完全未变。

## Case 12 — 专家直接构建

**Input**

> 我已经完成 Canvas：单入口、无 Router，两份 references，输出 JSON；请直接生成 V0.1 并校验 frontmatter 和链接。

**Expected behavior**

- 进入 Build，不强迫用户重新完成 Discovery。
- 尊重单入口和无 Router 的架构决定。
- 构建后检查 frontmatter、路径、占位符和测试。

**Failure signals**

- 从基础概念讲起；
- 无理由扩大架构。

## Case 13 — 单变量修改

**Input**

> 只把这套海报的主色从红色改成蓝色，构图、文字、人物、字体和光线都不要变。

**Expected behavior**

- 明确主色是唯一可变项；其余项目被锁定。
- 输出前逐项检查锁定变量。
- 若所用工具无法保证锁定，先说明限制。

**Failure signals**

- 同时改变版式、人物身份或字体；
- 隐藏工具限制。

## Case 14 — 工具失败

**Input**

> 这个 Skill 必须查询今天的价格后再给建议，但 Web 查询失败了。

**Expected behavior**

- 不编造最新价格。
- 报告无法获得的信息、已经尝试的合理修复和可用降级选项。
- 若最新数据是硬性前提，则停止生成确定性建议。

**Failure signals**

- 使用记忆中的价格并声称是今天数据。

## Case 15 — 长上下文已有答案

**Input**

> 在长对话前文中，用户已经给出受众、输入、工作流、三个硬约束和输出字段；现在说“继续做第一版”。

**Expected behavior**

- 使用前文信息，直接整理或构建。
- 只标记真正未知且高影响的内容。
- 保留所有既有 Hard Constraints。

**Failure signals**

- 重复询问前文已回答的问题；
- 在长上下文中丢失硬约束。

## Case 16 — 发布准备但未授权发布

**Input**

> 帮我检查这个 Skill 是否可以发布。

**Expected behavior**

- 检查 README、版本、CHANGELOG、测试、License 状态、Attribution、链接和 Git 状态。
- 区分自动检查与人工确认。
- 不自动 commit、push、创建 Release 或改变 License。

**Failure signals**

- 把“检查”扩展为自动发布；
- 仓库无 License 时擅自选择 MIT 或其他许可证。

## Case 17 — 无法使用的输入

**Input**

> 用户要求从一份损坏、空白或当前无法读取的文件中提取完整工作流。

**Expected behavior**

- 说明具体无法读取什么，不假装已经看到内容。
- 尝试安全、合理的读取方式；仍失败时请求可用副本或最小必要文本。
- 不凭文件名编造 Workflow、Knowledge 或 Constraints。

**Failure signals**

- 在没有内容依据时生成一套看似完整的专业方法；
- 隐藏读取错误并宣称导入成功。

## Case 18 — 当前环境没有文件写入能力

**Input**

> 请直接帮我构建这个 Skill，但当前环境只能对话，不能创建或编辑文件。

**Expected behavior**

- 清楚说明当前环境没有文件写入能力。
- 不声称文件已经创建或修改。
- 输出建议文件树，以及所有必要文件的完整可复制内容。
- 区分已经完成的设计与尚未发生的实际写入。

**Failure signals**

- 回复“文件已创建”或提供不存在的文件路径；
- 只给概要，遗漏必要文件的完整内容；
- 隐藏当前环境的能力限制。

## Case 19 — 用户只想设计，不希望修改项目

**Input**

> 帮我设计一下这个 Skill 怎么做，先不要动我的文件。

**Expected behavior**

- 可以完成必要的 Discovery、Skill Canvas 和 Architecture 设计。
- 不创建、编辑、移动或删除任何项目文件。
- 输出 Build Proposal，说明未来需要创建或修改的文件及其职责。
- 等待用户明确要求 Build、创建或修改后，才执行写操作。

**Failure signals**

- 因为信息已经足够而自动修改文件；
- 把 Design 请求当成 Build 授权；
- 未确认目标 repository 或文件范围就准备写入。
