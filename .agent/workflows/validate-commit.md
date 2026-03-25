---
description: "提交前验证 — 检查暂存文件中的硬编码值、设计文档章节完整性、JSON 有效性和 TODO 格式"
---

# 提交前验证

在执行 `git commit` 之前运行此命令，确保代码质量。

## 步骤

1. 检查当前暂存区是否有文件：
```bash
git diff --cached --name-only
```

2. 如果有暂存文件，逐项检查以下内容：

### 2.1 设计文档完整性
对 `design/gdd/` 下的 `.md` 文件，检查是否包含以下 8 个必需章节：
- Overview、Player Fantasy、Detailed、Formulas
- Edge Cases、Dependencies、Tuning Knobs、Acceptance Criteria

### 2.2 JSON 数据文件验证
对 `assets/data/` 下的 `.json` 文件：
// turbo
```bash
python3 -m json.tool assets/data/*.json > /dev/null 2>&1 && echo "JSON 验证通过" || echo "JSON 验证失败"
```

### 2.3 硬编码 Gameplay 值检查
对 `src/gameplay/` 下的代码文件，搜索可能的硬编码值：
```bash
grep -rnE '(damage|health|speed|rate|chance|cost|duration)[[:space:]]*[:=][[:space:]]*[0-9]+' src/gameplay/ 2>/dev/null
```
如果找到匹配项，提醒用户：这些值应该从配置文件中加载，不应该硬编码。

### 2.4 TODO/FIXME 格式检查
对 `src/` 下的代码文件，检查 TODO/FIXME 是否带有负责人标签：
```bash
grep -rnE '(TODO|FIXME|HACK)[^(]' src/ 2>/dev/null
```
如果找到匹配项，提醒用户使用 `TODO(name)` 格式。

3. 汇总所有发现的问题，向用户报告：
   - 🔴 **阻断项**（如无效 JSON）— 必须修复后才能提交
   - 🟡 **警告项**（如硬编码值、缺失章节）— 建议修复
