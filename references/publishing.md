# Publishing：负责任地准备发布

发布准备的目标是让别人理解、安装、验证和继续改进 Skill。它不代表自动 Push、创建 Release 或选择 License。

## 发布材料

### README

先解释它解决什么问题、适合谁、怎样用自然语言开始、会得到什么；再介绍结构与进阶用法。不要让 YAML、终端命令或架构图占据首屏。

### Version 与 CHANGELOG

新 Skill 从 V0.1 开始：

- V0.1：能够运行和测试；
- V0.2：修复明显问题；
- V0.5：工作流基本稳定；
- V0.8：公开测试；
- V1.0：经过验证的稳定版本。

CHANGELOG 记录实际能力变化，不只写“优化体验”。

### Credits 与 Attribution

使用他人项目、模板、方法或素材时：

1. 查看原项目 License；
2. 保留 License 要求的 Attribution；
3. 说明来源；
4. 说明自己修改了什么；
5. 遵守原 License 的限制。

这不是法律意见。License 不清楚时，标记为需要作者确认，不自行推断授权。

## Open Source 与真正的二次创作

鼓励：

`STUDY → UNDERSTAND → MODIFY → EXTEND → CREDIT → SHARE`

Fork 的价值不在换名字、换 Logo 后重新发布，而在理解原方法、加入自己的专业判断、开发新的能力并清楚说明修改。

## License Awareness

- 不默认所有 Skill 使用同一种许可证；
- 不自动新增或修改 `LICENSE`；
- 仓库没有 License 时，在 README 或发布报告中明确“尚待项目作者决定”；
- 需要具体法律判断时，建议咨询合格专业人士。

## Git 安全

发布前只做用户授权的 Git 操作：

- 检查 repository root、remote、branch 与 status；
- 查看完整 diff 和 diff summary；
- 确认没有跨仓库文件；
- 检查敏感信息、临时文件和未完成占位符；
- 不自动 commit、push、force push、改 visibility 或发布 Release。

## 最终检查

使用 [../templates/PUBLISH_CHECKLIST.md](../templates/PUBLISH_CHECKLIST.md)。报告自动完成的检查、只能人工确认的事项和剩余作者决策。不要把“文件存在”误报为“真实行为已经验证”。
