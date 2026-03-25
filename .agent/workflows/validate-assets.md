---
description: "资产文件验证 — 检查 assets/ 目录下文件的命名规范（小写+下划线）和 JSON 有效性"
---

# 资产文件验证

检查 `assets/` 目录下的文件是否符合命名规范和数据格式要求。

## 步骤

1. 扫描 `assets/` 目录下所有文件，检查命名规范：
```bash
find assets/ -type f 2>/dev/null | while read f; do
  basename "$f" | grep -qE '[A-Z[:space:]-]' && echo "命名违规: $f（应使用小写+下划线）"
done
```
规范要求：文件名必须是**全小写**，只能使用**下划线**分隔，不能包含空格或连字符。

2. 对 `assets/data/` 下的 JSON 文件进行有效性验证：
```bash
find assets/data/ -name "*.json" -type f 2>/dev/null | while read f; do
  python3 -m json.tool "$f" > /dev/null 2>&1 || echo "无效 JSON: $f"
done
```

3. 汇总报告：
   - 列出所有命名违规的文件
   - 列出所有无效的 JSON 文件
   - 如果全部通过，报告 ✅
