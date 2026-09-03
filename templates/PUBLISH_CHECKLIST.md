# Publish Checklist

## Skill

- [ ] `SKILL.md` 存在，frontmatter 中 `name` 与 `description` 合法。
- [ ] Description 同时说明能力与触发场景，没有空泛营销词。
- [ ] Purpose 与 V0.1 边界清晰。
- [ ] Workflow 包含真实步骤和关键决策。
- [ ] Hard Constraints 与 Preferences 已区分。
- [ ] Output 明确数量、字段或格式。
- [ ] Check 与 Repair 可以执行。
- [ ] references 均有读取条件，没有重复堆叠。

## Tests

- [ ] 标准、最少输入、缺失信息和冲突约束已覆盖。
- [ ] 初学者或专家场景按目标用户覆盖。
- [ ] 修改、工具失败或其他高风险场景已覆盖。
- [ ] 已修复已知失败，并重跑相邻回归场景。

## Documentation

- [ ] README 在首屏解释价值、适用人群和自然语言起点。
- [ ] README 链接与相对路径有效。
- [ ] Version 从 V0.1 开始，并与 CHANGELOG 一致。
- [ ] CHANGELOG 描述实际能力变化。
- [ ] 模板没有意外残留的占位符。
- [ ] Credits、来源与修改说明完整。

## License & Attribution

- [ ] 已检查当前 License 状态。
- [ ] 没有擅自新增或改变 License。
- [ ] 使用第三方内容时已查看原 License 并保留必要 Attribution。
- [ ] 不确定的法律问题已标记给项目作者决定。

## Repository

- [ ] Repository root、remote 与 branch 正确。
- [ ] `git status` 只包含预期文件。
- [ ] 已查看完整 `git diff` 与 diff summary。
- [ ] 没有敏感信息、临时文件或跨仓库修改。
- [ ] Markdown 链接和文件名大小写已检查。
- [ ] 未经明确授权没有 commit、push、force push、改 visibility 或发布 Release。

## Final Review

- [ ] 新用户能在 3 分钟内理解并开始使用。
- [ ] Skill 本身可用，而不只是教程完整。
- [ ] 自动检查、人工检查与剩余决策已在交付报告中分别说明。
