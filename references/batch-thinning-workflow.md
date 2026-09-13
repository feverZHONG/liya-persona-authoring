---
tier: T2  # T分级: T2=直接做 / T1=先请示 / T0=一律拒
---

# 批量减法 · 一次砍多个厚 SKILL.md

当有 10+ 个厚 skill 需要一次性减薄时，走流水线，不逐个构思。

## 流程

### 1. 排序
按行数降序（`wc -l SKILL.md`），最厚的先减。200 行以上的优先。

### 2. 按章节拆 references（不要整段 dump）

**不要**创建 monolithic `references/full-reference.md`——这是「换汤不换药」的反模式。

正确做法：用脚本按 `##` 章节自动拆分为多个 reference 文件。

```python
# 核心逻辑
sections = []
for i, line in enumerate(lines):
    if line.startswith('## '):
        sections.append((i, line.strip()))
# 按 ~80 行/2-3 section 分组
# 每组写 references/NN-descriptive-name.md
# 删除原 full-reference.md
# 更新 SKILL.md 引用表
```

经验值：411 行的 skill 拆成 7 个 reference，每个 22-124 行，按需查阅。

### 3. 写薄版模板（原 3）
每个薄版结构：
```
YAML frontmatter → 铁律 → 触发条件 → 核心表格 → 指向 references/
```
目标 ~25-35 行。

### 4. 批量写入
一次写 3-5 个，不停下来看原文（已备份在 references/ 下）。

### 5. 验证
抽查 2-3 个确认 references/full-reference.md 完整。

## 薄版 vs 原版内容分配

| 放 references/ | 留在 SKILL.md |
|:--------------|:--------------|
| 详细步骤说明（Step 1-7） | 做什么的一行描述 |
| 场景展开讨论 | 场景列表+去哪看 |
| 背景原理 | 一句话核心原则 |
| 踩坑完整案例 | 关键坑条目 |
| 完整命令参数参考 | 最常用命令示例 |
