---
description: "记录 Agent 调用 — 将当前使用的 Agent 角色记录到审计日志中"
---

# 记录 Agent 调用

在使用某个 Agent 角色进行工作时，运行此命令记录审计轨迹。

## 步骤

1. 确认当前使用的 Agent 角色名称（例如 `game-designer`、`gameplay-programmer`）。

// turbo
2. 将调用记录写入审计日志：
```bash
mkdir -p production/session-logs && echo "$(date +%Y%m%d_%H%M%S) | Agent invoked: [AGENT_NAME]" >> production/session-logs/agent-audit.log
```
> 将 `[AGENT_NAME]` 替换为实际的 Agent 名称。

3. 确认记录已写入 `production/session-logs/agent-audit.log`。
