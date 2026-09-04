# Evaluation

## Purpose / Test vs Eval

[行为测试](testing.md)检查“是否按照设计做事”；Evaluation（效果评测）检查“使用 Skill 是否真的让任务结果更好”。守规则是必要证据，但不能单凭格式合格或文件存在就宣称增加了能力。

## When Evaluation Is Worth It

用户问 Skill 有没有用、能否减少返工、是否优于不用 Skill 或旧版、要求 eval / benchmark / 效果优化时，进入本流程。单纯“哪里坏了”继续 [Review / Repair](debugging.md)，不强制整套 Benchmark。

Comparative Evaluation 不只用于 Skill vs no-skill 或 new Skill vs old Skill，也适用于同一个 Skill 内多个候选 Workflow / Output structure / strategy 之间的真实效果比较。

先利用已有意图、工作材料、成功标准和失败案例，只问影响比较的缺口。第一次通常选 2–3 个真实任务即可；简单 Skill 不必建立大型评测集、数据库、仪表盘或专属运行器。按需要选择 comparative evaluation、trigger evaluation、qualitative review，而非全套执行。

## Baselines

基线必须代表用户实际会使用的合理替代方案，而不是人为削弱的对手。

| 场景 | 主要比较 |
| --- | --- |
| 新 Skill | WITH SKILL vs BASELINE WITHOUT SKILL：同一任务与材料，不提供目标 Skill 的指令或隐性规则 |
| 改进已有 Skill | NEW SKILL vs OLD SKILL SNAPSHOT：以改动前的真实版本为主要 baseline；no-skill 可补充，但不能替代旧版比较 |

保持任务 Prompt、输入材料、可用工具、模型与环境尽量相同，记录无法控制的差异。唯一核心变量应是 Skill 是否存在或版本不同；不能给新版本额外提示、更多资料或更多重试却隐瞒差异。

## Evaluation Plan

先定义标准，再运行和查看结果。已有结果可供诊断，但若看到结果后才制定标准，报告为回顾性分析，并用未见任务重测，不伪称预先计划。

计划至少包含：

- **Skill goal**：什么实际能力或交付质量应该改善。
- **Baseline**：no-skill 或旧版来源、版本 / snapshot 标识及选择原因。
- **Eval prompts**：真实用户可能说的话及对应输入材料。
- **For each prompt**：Why this case matters、Expected behavior、Failure signals、适用的 Objective criteria 与 Qualitative review criteria；不适用项说明原因。
- **Run conditions**：模型、工具、环境、隔离方式、允许的重试与停止边界，以及持久文件是否得到授权。
- **Decision rule**：哪些差异构成增益或退化，哪些 Hard Constraints 不能被平均分掩盖；需要谁做主观判断。

不要求复杂 JSON 模板。可以在对话中用短表完成计划。若目标、旧版材料或关键标准缺失，先补最小缺口，不擅自换一个容易获胜的 baseline。

## Realistic Eval Prompts

优先选择真实历史请求或用户会自然说出的句子，保留常见的不完整表达与实际材料。通常覆盖典型任务、困难边界和已知失败；不要只用逐字提醒 Skill 规则的“完美输入”。

例如，评测客户投诉处理 Skill，可用真实匿名投诉与既有制度，观察是否识别升级条件，而不是要求模型“必须按 Skill 中第六条触发升级”。比较双方收到同样的用户信息，不能把评测答案泄漏给其中一方。

## Objective Criteria

可直接观察的条件适合定量或二元检查：文件是否实际创建、字段与格式、数量、Hard Constraints、重复提问、越界写入、锁定变量、正确路径。

每项结论引用实际输出或工具日志，并明确通过 / 失败 / 无法验证。若计算比例，说明分子、分母和计算方式；没有实际执行就没有 pass rate。客观条件不代表整体专业质量。

## Qualitative Review

写作、创意、审美、视觉方向差异与专业帮助程度，优先邀请用户或领域评审查看结果。客观约束仍可独立检查；不把“更长、更详细”默认当成更好。

可使用有具体含义的粗粒度量表，但不要制造伪精确数字。适合问：

- 哪份更像你真正会交付的结果，为什么？
- 哪份减少了返工，使用了你的真实判断？
- 哪些细节看起来丰富却没有帮助，或增加了不必要流程？

条件允许时用 A / B 盲评，不提前揭示版本；这只是建议。将用户判断与 AI 自评分开记录，AI 自评不能冒充用户认可。未获得必要人工反馈时保留待确认或 INCONCLUSIVE。

## With Skill vs Baseline / New vs Old Skill

执行前确认目标 Skill 是否自动加载、全局指令是否泄漏规则。no-skill 运行若仍加载同名 Skill，不能算有效 baseline；同名旧版冲突也不能靠口头声明解决。

旧版优先使用已有不可变 Git revision 或只读 snapshot，保留全部运行所需 references 等资源。不能先覆盖旧版，再把改后的文件当 baseline。创建持久 snapshot 需要 Write Gate 授权，读取已有旧版不等于允许修改它。

对每个任务分别生成双方输出；不把第一方的答案、评价或修复意见传给另一方。尽量使用独立上下文；只能顺序运行时仍保持相同条件并披露上下文污染风险。无法隔离时提供受限比较或计划，不冒充严格受控实验。

## Trigger Evaluation

先用少量真实表达和相邻请求做轻量 Trigger Review，不做自动 description optimizer：

- **SHOULD TRIGGER**：确实需要本 Skill，包括没有说“Skill”但意图明确的请求。例如“把我每次审核提案的判断整理成 AI 可重复执行的方法”。
- **SHOULD NOT TRIGGER**：相近关键词但不需要制作或评测 Skill。例如“按这个已经确定的拍摄计划给我一条图像提示词”。
- **AMBIGUOUS**：现有上下文不足以判断。例如“帮我优化一下这个流程”，但未提供对象；先澄清任务，不自动启动 Benchmark。

为每条输入预先写预期类别与原因，再观察实际是否被选择、是否读取正确 `SKILL.md`、是否走正确入口。区分漏触发和误触发，检查 description 是否过窄、过宽或只能靠显式名称触发。显式调用成功不证明隐式触发正确。

宿主不能提供选择日志或真实路由测试时，只能报告静态 Trigger Review / Not Executed，不能捏造触发准确率。必要时提出最小 description 修改，获得写入授权后实施，并重测应触发与相邻不应触发请求。

## Running When Tools Are Available

环境支持隔离运行、子 Agent 或并行执行，且获授权时，可以成对运行 Skill 与 baseline；这些不是必要依赖，也不要求专属 grader。无并行能力时可顺序运行。

运行前遵守 [Write Gate](../SKILL.md)：只分析现有结果或设计 Evaluation Plan 不写文件。明确请求实际执行且目标范围清晰后，才可创建持久 workspace、snapshot、outputs、测试文件或 benchmark。只说“看看”“继续”不是授权；允许评测也不等于允许修复 Skill、安装依赖、发布或修改外部系统。

可完全在临时 / 非用户文件环境执行时，说明真实隔离与保存状态，并服从用户更严格的禁止写入要求。不借测试执行真实付款、发送消息等外部操作；需要这些动作时使用获准的安全模拟或停下请求具体授权。

保留每方版本、实际输入、输出和必要执行证据。失败按预先约定的合理重试界限处理；单边工具失败或环境不一致影响可比性时报告，而不是偷偷替换样本。

## Running When Tools Are Unavailable

无法实际运行目标 Skill 时，输出 **Evaluation Plan** 和 **How to Run It**：说明需要的两种配置、同一组输入、预定标准、如何独立运行并带回结果。明确 **Not Executed**。

仅完成一方时标记部分执行；另一方未运行、缺失输出或关键反馈时，比较通常为 INCONCLUSIVE。不虚构结果、pass rate、time、tokens、cost 或工具次数。

## Interpreting Results

逐 Case 判断，再给出有限范围的整体结论，不隐藏失败样本：

| 结果 | 证据要求 |
| --- | --- |
| ADDS VALUE | 在预定关键标准上有可观察改善，且没有被重要退化抵消 |
| NEUTRAL | 比较可完成，但没有明显优势；可能只增加了文字或流程 |
| REGRESSION | 关键质量、约束、用时或流程负担更差；即使其他项通过也要报告 |
| INCONCLUSIVE | 证据缺失、不可比、波动过大，或尚缺必要的人类判断 |

一组小样本的结论只适用于被测任务，不能保证普遍有效。质量与效率取舍按预定目标解释，不默认自己写的 Skill 一定有用。结果波动时建议复跑或补一个有区分力的真实任务，不立即制造 50 个 eval。

仅当宿主真实提供可靠 tokens、duration、cost、tool count 时才记录，并注明来源；缺失就写不可用，不把猜测、输出长度或工具墙钟时间包装成总成本。性能是辅助指标，不能在没有计算依据时说“质量提升 37%”。

## Repair and Retest

`PROBLEM → ROOT CAUSE → MINIMUM CHANGE → RETEST`

依据实际输入、输出与日志，把失败映射到 Trigger、Routing、Workflow、Knowledge、Constraints、Output、Check 或 Repair，定位最早的错误。不要简单追加更长 Prompt，不把单个案例硬编码为规则。

先给最小修复建议；明确授权修改后只改相关模块，保留旧 baseline。至少重跑失败 Case 和相邻 Regression Case，比较仍使用相同基线与标准。若改了评测标准，记录原因并重新评测双方；不能为了新版本获胜移动标准。无法重跑就报告 Retest Not Executed，不声称修复已证实。

## Reporting

报告目标、baseline 来源、预先约定的任务与标准、实际执行范围、证据、逐 Case 与整体结论、用户反馈、剩余不确定性和下一步最小动作。

分开写清：Behavioral Testing 结果、Comparative Evaluation 结果、Trigger Review / 实际触发测试、人工 Review 状态。未经执行的部分标记 Not Executed；只有实际可核验数据才列 metrics。无需额外平台、API、脚本或第三方 Skill 才能采用此方法。
