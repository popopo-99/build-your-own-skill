# 已有 Skill 不好用，怎么修？

*Review → Repair*

## 起点

用户已经有一个能运行的 `SKILL.md`。问题不是“怎么做一个新 Skill”，而是它为什么表现不稳定：会重复询问已经提供的信息，简单任务也走复杂流程，只修改一个变量时其他内容却发生漂移。

用户明确要求先诊断根因，不直接重写整个 Skill，不修改文件，并按最小修改（Minimum Change）原则处理。

## Review 模式做了什么

本次没有返回 Discovery 重新采访，而是按已有 Skill 的诊断路径处理：

```text
AUDIT
→ PROBLEM
→ ROOT CAUSE
→ MINIMUM CHANGE
→ TEST
```

先观察行为，再判断它属于哪一层；只有确定根因后，才提出限定范围的修复和回归测试。

## 三个症状分别属于哪一层

### 重复问已经提供的信息

- **主要层：Workflow**
- **次要层：Check / Repair**
- **根因**：Skill 虽然写了使用 supplied information，但没有明确规定提问前扫描已有上下文并去重。

这不是知识缺失，也不需要改 Trigger。需要的是在提问动作前增加可执行的上下文检查，并在返回前确认没有重复提问。

### 简单任务也走复杂流程

- **主要层：Workflow**
- **根因**：所有请求共用固定完整流程，没有轻量路径。

修复重点是按任务复杂度选择路径，让信息已经充分或请求很简单的任务直接进入轻量执行，而不是为它新增更多访谈问题。

### 修改一个变量造成漂移

- **主要层：Constraints**
- **次要层：Check / Repair**
- **根因**：虽然已有 `lock all others`，但缺少可验证的 `baseline → requested delta → locked remainder → diff check`。

仅靠一句“锁定其他内容”不够；需要把基线、请求变化和保持不变的部分明确分开，并在输出前做差异检查。

## 哪些地方不应该动

诊断没有发现需要改动以下部分：

- Trigger
- Permanent visual DNA
- Knowledge reference
- calibration example
- Output 主结构
- 主要质量检查
- 文件架构

Minimum Change 的价值不是“哪里都优化一点”，而是只修改真正导致问题的层。扩大到这些稳定部分会增加新回归风险，也会掩盖当前根因。

## 最小修复方案

本轮把建议整理为四个 patch，但没有执行写入：

1. **Inputs**：增加提问前的上下文扫描，先提取用户已经给出的时间、天气、人物等信息。
2. **Workflow**：增加轻量任务路径，让简单且信息充分的请求跳过复杂访谈。
3. **Constraints**：把单变量编辑升级为 `baseline → requested delta → locked remainder`。
4. **Check / Repair**：增加提问去重与 diff verification，发现无关漂移时只修漂移部分。

完整诊断见 [`diagnosis.md`](diagnosis.md)。

## 回归测试

建议的回归测试直接对应三个根因：

- 用户已经给过时间、天气和人物时，不得再次询问。
- 简单场景请求不应启动复杂访谈。
- 用户只要求修改丝绸颜色时，其他变量必须保持。

这些是待修复后执行的测试方案，不是已经通过的测试成绩。

## 为什么没有直接修改文件

这是一个真实的 Review-only 案例。用户没有授权写入，因此 Build Your Own Skill 只输出诊断和最小修复建议，没有创建、修改或打包文件。

没有写入不是“没有完成任务”，而是正确遵守 Review 边界和 Write Gate。Case 03 因此也没有伪造 `before/`、`after/` 或 patched `SKILL.md`。

## 这个案例教会了什么

- 调 Skill 不等于重写 Skill。
- 症状不等于根因，要先判断故障属于哪一层。
- Minimum Change 能保护已经稳定的 Trigger、知识和输出结构。
- 单变量锁定需要可验证的基线与差异检查。
- 修复完成后必须运行针对根因的回归测试。
