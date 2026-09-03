# Workflow Design：把隐性经验变成显性流程

Workflow Extraction（工作流提取）的核心问题不是“AI 应该怎么做”，而是“有经验的人实际怎么做，以及为什么这样做”。

## 提取方法

选择一个最近的真实任务，按时间线还原：

1. 收到了什么输入；
2. 首先观察了哪些信号；
3. 做了哪些判断；
4. 采取了哪些行动；
5. 哪些条件导致分支或返工；
6. 如何确认完成。

把动作和判断分开记录。动作是“整理竞品截图”，判断是“哪些竞品与本品牌处在同一价格带”。后者通常更接近有价值的专业知识。

## 一个可选的基础骨架

`INPUT → ANALYZE → PLAN → EXECUTE → CHECK → REPAIR → OUTPUT`

这只是检查遗漏的骨架，不是所有 Skill 的固定格式。若用户真实流程更短、更循环或有特殊顺序，应保留真实结构。

## 把描述改成可执行步骤

较弱：

> 深入分析品牌并提供有创意的方向。

较强：

> 从 Brief 提取品牌阶段、受众、价格带和必须保留的资产；列出同类常见视觉套路；为每个方向选择不同的核心张力；生成后检查三个方向是否只换了颜色，若是则重做重复方向。

可执行流程通常包含：输入、观察对象、决策条件、动作、产物和检查。

## 真实职业示例

### 设计

`READ BRIEF → BRAND STAGE → AUDIENCE → COMPETITORS → VISUAL TENSION → DIRECTIONS → DIFFERENTIATION CHECK → REPAIR → PROPOSAL`

关键不在步骤名称，而在“视觉张力如何选”“何时认为方向重复”等判断。

### 摄影

`READ SHOOT GOAL → INSPECT SUBJECT/LOCATION → IDENTIFY TIME-SENSITIVE RISKS → SHOT ORDER → LIGHTING PLAN → SHOOT CHECKLIST → CONTINGENCY`

若食物状态变化快，拍摄顺序可能比器材选择更重要。

### 运营

`GOAL → AUDIENCE SIGNALS → CONTENT INVENTORY → TOPIC FILTER → PRIORITY → DRAFT → PLATFORM CHECK → REVIEW`

要提取的是选题过滤条件，而不是让 AI 泛泛“研究用户”。

### 程序开发

`REPRODUCE → LOCATE BOUNDARY → FORM HYPOTHESIS → MINIMUM CHANGE → TARGETED TEST → REGRESSION CHECK → HANDOFF`

应明确什么证据能否定假设，以及何时停止扩大修改范围。

## 分支、循环与停止条件

工作流不一定是直线：

- **分支**：输入类型不同，处理方法是否真的不同？
- **循环**：检查失败后，回到哪一步？
- **停止**：什么条件表示信息足够或结果通过？
- **升级**：哪些情况需要用户决策、人工专家或外部工具？

只有存在两条以上实质不同的流程时才需要 Router。轻微差异可在同一工作流内用条件规则处理。

## 提取检查

- 是否来自真实案例，而非听起来专业的虚构步骤？
- 是否包含关键判断，而不只有动作？
- 是否写明输入不足时怎么办？
- 是否保留不能跳过的检查？
- 是否能解释失败后回到哪一步？
- 输出是否与流程直接对应？

无法回答的部分可以标记为待测试假设；不要用空泛术语填补。
