---
name: your-skill-name
description: Describe what this Skill does and the user request that should activate it.
---

# Your Skill Name

用一句话说明这个 Skill 帮用户稳定完成什么任务。

## When to use

在用户需要以下结果时使用：

- 写出一个具体触发场景；
- 若容易误触发，写出一个清晰边界。

## Inputs

开始前，从用户已有信息中提取：

- 必需输入：缺少就无法可靠继续；
- 可选输入：缺少时可以采用合理假设。

只询问会实质改变结果的问题。不要让用户填写机械问卷。

## Workflow

1. 检查输入与硬约束。
2. 按用户真实方法分析关键变量。
3. 根据条件做出必要选择。
4. 生成约定的结果。
5. 对照质量标准检查；失败时修复并再次检查。

把这些通用句改成该职业真实使用的步骤和决策规则。

## Constraints

- Hard Constraint：写出绝对不能违反的规则。
- Preference：写出允许按上下文调整的偏好。
- 如果用户只要求修改一个变量，锁定其他变量。

## Output

明确写出交付物的数量、结构和必要字段。不要只写“给出高质量建议”。

## Quality Check

输出前确认：

- 必需输入和用户要求已被使用；
- 所有 Hard Constraints 已满足；
- 结果具体、可执行，没有无依据的信息；
- 输出结构完整；
- 若发现问题，已修复并重新检查。

## Before using this template

删除所有教学提示和占位内容。V0.1 不需要默认添加 Router、scripts、API 或数据库；只有真实任务证明需要时再增加。
