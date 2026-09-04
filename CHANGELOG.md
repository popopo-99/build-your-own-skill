# Changelog

All notable changes to this project will be documented in this file.

## V0.3.0 — Deep Discovery & Evaluation

日期：2026-09-05

### Added

- **Deep Discovery（深度发现）**：当用户明确希望深入梳理经验时，逐步提取隐性知识；每轮只问少量真正会改变设计的问题。信息足够时停止，无法靠继续提问解决的问题转向 Research / Prototype / Evaluation。Quick Discovery 仍是默认。
- **Evidence-aware decisions / Comparative Evaluation（重视证据的决策与比较评测）**：
  - 区分 USER-ANSWERABLE、RESEARCHABLE、TESTABLE / PROTOTYPABLE 和 DEFERRABLE，不把“我不知道”统一理解为需要继续采访。
  - 支持新 Skill 与无 Skill、新版与旧版，以及候选 A 与候选 B 的真实任务比较；主观任务也可使用有依据的定性评审。
  - 使用 ADDS VALUE、NEUTRAL、REGRESSION 或 INCONCLUSIVE 表达比较结果；无法实际执行时明确 Not Executed，不把测试计划或推测冒充结果。
- **Evidence Boundary（证据边界）**：在 V0.2 已有 Knowledge Provenance 的基础上，区分“用户真实经验 / 系统推断 / 系统建议”的来源与支持优劣判断的实际证据。不把 AI 补充的方法冒充用户多年经验，也不把“这是谁提出的”当成“凭什么说它更好”的答案。
- **Tutorial Case Studies（教学案例）**：新增 Visual Designer、AIGC Short Drama Director、Cafe Manager 三个跨行业教程，展示 Skill 可以来自任何职业的重复判断和经验；职业场景经过匿名化、改写或教学化处理，不代表职业方法已获效果验证。
- **Expanded Behavioral Tests**：行为案例扩展到 41 个场景；案例覆盖不等于所有 Runtime 测试通过。
- **授权与来源文件**：加入 Apache License 2.0、Commons Clause License Condition v1.0 和 NOTICE，说明商业使用、再分发及独立产出内容的边界。

### Changed

- Discovery 的停止条件更清晰：只继续澄清会改变设计的未知项，不为完整问卷而追问。
- Write Gate 明确覆盖 Deep Discovery 与 Evaluation；访谈、设计和评测准备不自动授权文件写入。
- 区分 Behavioral Testing（是否遵循行为契约）与 Evaluation（是否带来实际增益）；Review / Repair 可按需使用比较结果，不强制完整 Benchmark。
- README 加入跨行业使用入口，改进教程、案例与评测导航，并保留设计启发来源。

### Known Limitations

- **Known limitation / non-blocking adversarial behavior**：在极端 adversarial forced-choice 场景中，用户要求即使没有比较证据也必须临时选择 A/B，Runtime 仍可能产生 provisional recommendation。普通 TESTABLE 决策流程已能识别需要真实比较的情况，但极端强制选择的一致性仍受模型运行时行为影响。

## V0.2.0 — 2026-09-04

### Added

- Strict Write Gate.
- Knowledge Provenance:
  - USER-DERIVED
  - INFERRED
  - PROPOSED
- Behavioral tests for ambiguous Build authorization.
- Behavioral test preventing AI suggestions from being presented as user-derived knowledge.

### Changed

- Discovery / Design / Review now remain read/design-only until explicit Build authorization.
- Ambiguous responses such as “继续 / 好 / 可以 / 下一步” no longer authorize file writes.
- Important inferred or proposed rules must disclose their source before becoming core Workflow, Hard Constraints, Router logic, or important quality standards.
- Updated existing behavioral test wording to remove ambiguous Build authorization.

## V0.1.0 — 2026-09-04

Initial testable release of Build Your Own Skill.

### Added

- Core Skill Builder architecture and stage-aware entry flow.
- Discovery system for repeated problems and tacit knowledge extraction.
- Scope definition, Skill Statement, and Skill Canvas guidance.
- Workflow and professional knowledge extraction methods.
- Minimum necessary architecture and progressive disclosure guidance.
- Testing, self-check, repair, and Skill Doctor guidance.
- Beginner-ready Skill Canvas, basic Skill, and publishing templates.
- `brand-visual-director` teaching example.
- Behavioral test cases for beginner, expert, import, review, failure, and overengineering scenarios.
- Chinese-first README and long-term repository maintenance rules.
