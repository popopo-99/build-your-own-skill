# Review / Repair Diagnosis

本文件整理一次真实的静态诊断。该轮没有获得文件写入授权，因此以下内容是根因分析、最小修复方案与待执行的回归测试，不代表修复已经实施或验证通过。

## Observed Problems

1. Skill 会重复询问用户已经在上下文中提供的信息。
2. 简单任务也会启动完整的复杂流程。
3. 用户只修改一个变量时，其他内容会发生漂移。

## Layer Diagnosis

| Observed problem | Primary layer | Secondary layer |
| --- | --- | --- |
| 重复问已经提供的信息 | Workflow | Check / Repair |
| 简单任务也走复杂流程 | Workflow | — |
| 单变量修改造成其他内容漂移 | Constraints | Check / Repair |

## Root Causes

### 重复提问

现有 Skill 提到应使用 supplied information，但没有把“提问前扫描已有上下文并去重”写成必须执行的步骤，也没有在检查阶段验证新问题是否已经被回答。

### 流程过重

标准请求、最少输入和简单修改共用一条固定完整流程。Skill 没有根据请求复杂度、已有信息量或任务类型进入轻量路径的明确条件。

### 单变量漂移

现有 `lock all others` 是意图声明，不是可检查的修改协议。缺少变更前基线、唯一允许变化的 requested delta、其余 locked remainder，以及输出后的 diff check。

## Minimum Changes

### Patch 1 — Context scan before questions

在 Inputs 或提问步骤前加入上下文扫描：先列出当前对话和用户材料已经提供的字段，只询问会实质改变结果且尚未回答的信息。

### Patch 2 — Lightweight workflow path

在 Workflow 中增加轻量分支：当任务简单、输入充分或只是局部修改时，跳过完整访谈，直接执行相应的小范围流程。

### Patch 3 — Verifiable single-variable edit

把单变量修改明确为：

```text
baseline
→ requested delta
→ locked remainder
→ revised output
```

只允许 requested delta 变化，其余已存在内容构成 locked remainder。

### Patch 4 — Question deduplication and diff verification

在 Check / Repair 中增加两项检查：新问题是否已经被上下文回答；修改结果是否只改变 requested delta。若发现重复问题或无关漂移，只修对应模块。

## Areas to Preserve

以下部分没有证据表明是当前根因，不应在这轮修改：

- Trigger
- Permanent visual DNA
- Knowledge reference
- calibration example
- Output 主结构
- 主要质量检查
- 文件架构

保留这些部分可以避免把局部行为故障扩大成全盘重写。

## Regression Tests

### 已有信息不得重复询问

**Input**：上下文已经给出时间、天气和人物。

**Expected**：直接使用这些信息；只在仍有关键冲突或缺失时提出新问题，不重复问时间、天气或人物。

### 简单场景走轻量路径

**Input**：一个信息足够、没有冲突的简单场景请求。

**Expected**：不启动复杂访谈或完整 Discovery；使用轻量流程完成请求。

### 只修改丝绸颜色

**Input**：在已有结果中只修改丝绸颜色。

**Expected**：记录原结果为 baseline，把颜色作为 requested delta，锁定其余构图、人物、建筑、摄影机、光线、材质和风格；diff check 不得发现无关变化。

这些测试尚未在修复后运行。本案例只完成了静态诊断与测试设计。
