# 从长 Prompt 到 Skill：仙侠天界 Image 2

*Prompt → Skill*

## 起点

用户已经有一条长期使用、能够产生不错结果的仙侠天界 Prompt。它不是失败 Prompt；问题是随着经验不断加入，它越来越长，也越来越难维护。

原始 Prompt 被完整保存在 [`original-prompt.md`](original-prompt.md)。

## 为什么不能只加 frontmatter

给长 Prompt 加一段 frontmatter 只能让它看起来像 Skill，不能让隐含决策变得可执行。原 Prompt 同时混合了场景内容、摄影机、构图、建筑知识、视觉判断、Hard Constraints、Preferences、材质、光线和修饰词，但没有显式 Workflow，也没有清楚说明失败后检查什么、只修哪一层。

Skill 需要把一次成功描述中的稳定方法与本次场景变量分开，明确输入、优先级、流程、输出、检查和修复。否则 Prompt 只会继续增长。

## Import / Learn 如何拆解 Prompt

Build Your Own Skill 从 **Import / Learn** 入口读取已有材料，并把内容拆成：

- **Trigger**：用户何时需要仙侠天界 Image 2 Prompt。
- **Workflow**：从场景提取、空间与摄影机安排，到编译和复查。
- **Professional Judgment**：真实空间、遮挡、宏大感、中国性、奇幻层级和观察感。
- **Generic Knowledge**：`cinematic`、`high quality` 等不能代表用户独特方法的通用表述。
- **Hard Constraints**：所有场景都必须保留的视觉 DNA。
- **Preferences**：随场景权衡的光线、色彩、天气、颗粒和装饰程度。
- **Output**：面向 GPT Image 2 的英文 Prompt 与生成设置。
- **Check / Repair**：逐项检查稳定视觉 DNA、空间、层级、光线和漂移，只修失败模块。
- **References**：详细视觉 DNA 与校准示例。
- **Duplicate / Conflict / Redundant Content**：重复、冲突、指代或空间歧义。

## Prompt 中真正值得保存的是什么

值得保存的不是更多 `cinematic` 或 `high quality`，而是原 Prompt 里能够迁移到其他仙侠天界场景的判断：

- 摄影机必须能在真实空间中存在。
- 遮挡必须有现实动因，而不是贴在画面边缘。
- 宏大感来自尺度、负空间、空间层次和小人物活动，而不是建筑堆砌。
- 中国性来自屋顶、斗拱、梁柱、台基等建筑结构，而不是文字。
- 奇幻母题必须服从视觉层级，瓷质神像浮雕不能抢走主体。
- 画面应当是 `observant rather than staged`，像被观察到的真实时刻，而不是正中摆拍的海报。

## 如何发现 Prompt Spaghetti

分析没有把“长”本身当作错误，而是定位了会增加维护成本的具体问题：

- `blank plaque` 与 `no text` 重复表达无文字要求。
- cloud 相关描述分散在空间、遮挡、光线和气氛中。
- `restrained` 多次重复，部分位置可以改成更具体的层级或材质关系。
- `soft heavenly daylight` 与 `pale dawn light` 需要合并成一个一致的主光源。
- `concealed corridor` 引入了未建立的空间，摄影机位置存在歧义。
- `metallic-white porcelain` 容易在金属与瓷之间产生材质歧义。
- `pale silver joints` 没有说明连接的具体对象。
- 唐宋混合语言需要说明是统一的天界谱系，而非严格历史复原。
- 丝幡既承担前景遮挡，也可能与主体可读性竞争。

这些发现被转化为明确的约束优先级、参考说明和最小修复规则，而不是简单删短 Prompt。

## 三个关键确认问题

本次设计最终确认了三个会实质改变 Skill 的问题：

1. **Scope**：所有仙侠天界场景。
2. **永久视觉 DNA**：`21:9`、丝幡、唐宋建筑、瓷质浮雕、无文字。
3. **Target model**：GPT Image 2 / `image2`。

确认这三点后，Discovery 不再继续扩张，设计可以进入最小架构。

## Knowledge Provenance

- **USER-DERIVED**：真实原 Prompt、长期有效的视觉判断，以及用户确认的 Scope、五项永久视觉 DNA 和目标模型。
- **INFERRED**：从原 Prompt 的重复与案例关系中归纳哪些元素是跨场景不变量、哪些只是当前天门场景变量，并指出材质、空间、光源和指代歧义。
- **PROPOSED**：显式 Workflow、约束优先级、输出章节、Check / Repair、按需 reference 与平台元数据结构。

推断和补充建议没有被冒充为用户原有说法。尤其当它们成为核心 Workflow 或重要质量标准时，会说明其来源与作用。

## Write Gate

这次案例也真实验证了 V0.2 的写入门槛（Write Gate）。当用户说：

> 先帮我分析和设计，不要创建、修改或打包任何文件

系统只完成分析与设计，没有创建文件。只有在用户明确说：

> 按这个设计开始创建 Skill 文件

之后才进入 Build。设计已经完成、信息已经足够，都不等于获得写入授权。

## 最终架构为什么这样拆

- [`final/SKILL.md`](final/SKILL.md)：负责编排输入、永久约束、核心工作流、输出与检查修复。
- [`final/references/celestial-visual-dna.md`](final/references/celestial-visual-dna.md)：保存需要按场景查阅的详细放置、材质、优先级和定向修复规则。
- [`final/examples/heavenly-gate-reference.md`](final/examples/heavenly-gate-reference.md)：保存真实成功 Prompt，作为校准案例，而不是所有场景都要复制的模板。
- [`final/agents/openai.yaml`](final/agents/openai.yaml)：保存平台 / UI 元数据。它不是用户的方法论，也不是 Skill 核心逻辑。

这种拆分把主入口保持在可读范围内，同时没有引入 scripts、API 或不必要的 Router。

## 从原 Prompt 到 Skill，真正发生了什么

```text
Long Prompt
↓
Explicit Workflow
↓
Permanent Visual DNA
↓
Preferences
↓
Check / Repair
↓
Reference Example
↓
Reusable Skill
```

变化不只是文件变多，而是稳定知识、场景变量和质量控制第一次被显式分开。

## 这个案例教会了什么

- 有效的长 Prompt 不是废料，而是一份待拆解的经验容器。
- Skill 不是“更长的 Prompt”，而是可触发、可执行、可检查和可修复的方法。
- 永久视觉 DNA 必须与单个成功案例中的偶然变量分开。
- Prompt Spaghetti 应按重复、冲突和歧义诊断，而不是机械压缩。
- 分析完成不代表可以写文件；Build 必须获得明确授权。
