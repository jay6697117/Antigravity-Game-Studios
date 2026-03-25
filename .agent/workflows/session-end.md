---
description: "会话结束记录 — 记录本次工作的提交、未提交变更，归档会话状态"
---

# 会话结束记录

在结束一天的工作前运行此命令，记录工作进度。

## 步骤

// turbo
1. 运行会话结束脚本：
```bash
bash .agent/hooks/session-stop.sh
```

2. 脚本会自动：
   - 记录最近 8 小时内的 Git 提交
   - 记录当前未提交的文件变更
   - 归档活跃会话状态文件（`production/session-state/active.md`）
   - 将所有信息写入 `production/session-logs/session-log.md`

3. 向用户确认会话已记录：
   > ✅ 会话已记录到 `production/session-logs/session-log.md`
