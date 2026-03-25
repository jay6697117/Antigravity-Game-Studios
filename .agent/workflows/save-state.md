---
description: "保存会话状态 — 在上下文压缩前记录当前工作进度、修改文件和 WIP 设计文档"
---

# 保存会话状态

在长时间工作时运行此命令，保存当前工作状态到文件，防止上下文丢失。

## 步骤

// turbo
1. 运行状态保存脚本：
```bash
bash .agent/hooks/pre-compact.sh
```

2. 脚本会输出并记录以下信息：
   - **活跃会话状态** — 从 `production/session-state/active.md` 读取
   - **已修改文件** — 未暂存 / 已暂存 / 新增的文件列表
   - **WIP 设计文档** — 包含 TODO/WIP/PLACEHOLDER 标记的设计文档

3. 记录会被写入 `production/session-logs/compaction-log.txt`

4. 建议用户：
   - 如果 `production/session-state/active.md` 不存在，考虑创建它来记录当前工作要点
   - 下次恢复工作时，运行 `/session-context` 来加载上下文
