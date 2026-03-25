# 安全与权限参考

> 从 Claude Code `settings.json` 转换而来的安全规则参考文档。
> 在 Antigravity 环境中，这些规则作为开发指南参考，不会自动强制执行。

---

## ✅ 安全操作（可自由执行）

以下操作被视为安全的，可以放心执行：

- `git status` — 查看仓库状态
- `git diff` — 查看文件差异
- `git log` — 查看提交历史
- `git branch` — 查看/管理分支
- `git rev-parse` — Git 引用解析
- `ls` / `dir` — 列出目录内容
- `python -m json.tool` — JSON 格式验证
- `python -m pytest` — 运行测试

---

## 🚫 危险操作（必须谨慎）

以下操作可能造成不可逆的损害，**执行前务必确认**：

| 命令 | 风险 |
|------|------|
| `rm -rf` | 递归删除文件，不可恢复 |
| `git push --force` / `git push -f` | 强制推送，可能覆盖他人代码 |
| `git reset --hard` | 丢弃所有未提交的修改 |
| `git clean -f` | 删除未跟踪的文件 |
| `sudo` | 提权操作 |
| `chmod 777` | 开放所有权限，安全风险 |

---

## 🔒 敏感文件保护

以下文件**禁止读取或写入**：

- `.env` 及所有 `.env.*` 文件（包含 API 密钥、密码等敏感信息）
