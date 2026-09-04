# Testing：用真实行为验证 Skill

测试的目标是验证 Skill 是否在不同条件下做出正确决策，而不是检查它是否重复某个固定句子。

## Testing vs Evaluation

行为测试（Testing）回答“是否按照设计做事”；效果评测（Evaluation）回答“用了 Skill 是否真的更好”。通过全部行为测试，不等于已经证明增益。

只检查路由、格式、授权或约束时，继续使用本文件的 Input / Expected behavior / Failure signals。用户希望比较不用 Skill 或旧版结果、评价主观质量或优化触发效果时，按需阅读 [evaluation.md](evaluation.md)。不把普通 Review / Repair 自动升级成完整 Benchmark，也不在这里重复评测流程。报告应区分静态契约复查、实际行为运行和比较评测，未运行的项目不能记为通过。

## 建议场景

按风险选择最小覆盖集：

| 场景 | 要验证的行为 |
| --- | --- |
| Standard | 典型输入能完成完整流程 |
| Minimal Input | 只问真正必要的问题，不编造信息 |
| Missing Information | 识别高影响缺口并合理降级 |
| Conflicting Constraints | 发现冲突，优先硬约束并请求必要决定 |
| Bad Input | 不伪装理解，不产出无依据结果 |
| Expert User | 跳过已知基础，直接进入架构或构建 |
| Beginner User | 用普通语言推进，不要求代码知识 |
| Modification | 只修改指定变量，锁定其他部分 |
| Failure | 工具或流程失败时诚实报告并合理修复 |
| Long Context | 利用已有信息，不重复询问或遗忘关键约束 |

并非每个 Skill 都必须创建十个测试文件，但必须覆盖正常路径和最可能失败的非完美路径。

## 测试维度

### Trigger

该使用时是否被识别？相似但不相关的请求是否被错误吸引？

### Routing

不同入口是否进入正确流程？已有 `SKILL.md` 是否进入 Review 而非重新 Discovery？

### Instruction Following

是否遵守用户明确要求、顺序和授权边界？

### Quality

结果是否具体、可执行、有依据，并真正使用用户的方法？

### Consistency

相似输入是否遵循稳定规则？不同方向是否在要求的维度上真实不同？

### Edge Cases

缺失、冲突、异常格式、失败工具和超长上下文是否有合理处理？

### Output Contract

交付物数量、字段、格式和解释是否完整？

### Constraints

Hard Constraints 是否全部满足？Preferences 的偏离是否有理由？单变量修改是否锁定其余变量？

### Repair

发现问题后是否定位、修复并重新检查，而不是只提示风险？

## 测试用例格式

```markdown
## Case: 简短名称

**Input**
用户的真实请求和必要附件。

**Expected behavior**
- 应进入的模式；
- 必须做出的关键判断；
- 必须遵守的约束；
- 预期交付物。

**Failure signals**
- 可观察的错误行为。
```

避免只写“输出应该高质量”。让失败信号可观察，例如“立即生成 SKILL.md”“一次询问 15 个字段”“只换颜色却称为三个方向”。

## Check → Repair → Recheck

1. 根据 Output 和 Constraints 建立检查项；
2. 运行代表性用例并记录失败；
3. 把失败归因到 Trigger、Router、Workflow、Knowledge、Constraint、Output、Check 或 Repair；
4. 只改对应模块；
5. 重跑失败用例和相邻回归用例；
6. 记录版本变化。

不要为了通过测试硬编码某个示例措辞。修复应改善一类相同根因的问题。

## V0.1 通过标准

- 标准场景可完整走通；
- 最少输入不会被机械问卷淹没；
- 冲突和失败不会被隐藏；
- 输出格式与硬约束稳定；
- 已知问题有记录，且没有被虚假声明为完成。
