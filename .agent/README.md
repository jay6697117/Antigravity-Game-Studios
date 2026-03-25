# Antigravity Game Studios — 使用指南

> 从 Claude Code Game Studios 适配而来的 AI 游戏开发团队系统。
> 48 个 Agent 角色 · 37 个工作流命令 · 8 个自动化脚本 · 11 个编码规范

---

## 📂 目录结构

```
.agent/
├── agents/      # 48 个 Agent 角色定义
├── workflows/   # 37 个工作流（斜杠命令）
├── hooks/       # 8 个自动化脚本
├── rules/       # 11 个编码规范
└── README.md    # 本文件
```

---

## 🤖 使用 Agent 角色

Agent 角色文档定义了各职位的职责、决策框架和协作协议。

### 团队层级

| 层级 | Agent | 说明 |
|------|-------|------|
| **总监** | `creative-director`, `technical-director`, `producer` | 最高级别决策者 |
| **主管** | `game-designer`, `lead-programmer`, `art-director`, `audio-director`, `narrative-director`, `qa-lead`, `release-manager`, `localization-lead` | 部门负责人 |
| **专家** | 37 个专业角色 | 涵盖程序、设计、美术、音频、QA、运维等 |

### 使用方式

在对话中引用 Agent 文件获取专业指导：
- 查阅 `.agent/agents/creative-director.md` 了解创意方向决策框架
- 查阅 `.agent/agents/gameplay-programmer.md` 了解 gameplay 编码规范
- 查阅 `.agent/agents/game-designer.md` 了解游戏设计方法论

---

## ⚡ 使用工作流（斜杠命令）

在对话中输入 `/命令名` 即可触发对应工作流。

### 常用命令

| 类别 | 命令 | 说明 |
|------|------|------|
| **入门** | `/start` | 引导式新手流程 |
| **创意** | `/brainstorm` | 游戏概念头脑风暴 |
| **设计** | `/design-system` | 逐章节撰写 GDD |
| **审查** | `/code-review` | 代码质量审查 |
| **审查** | `/design-review` | 设计文档审查 |
| **生产** | `/sprint-plan` | 冲刺计划制定 |
| **平衡** | `/balance-check` | 游戏平衡性检查 |
| **发布** | `/release-checklist` | 发布前清单 |
| **团队** | `/team-combat` | 协调战斗系统团队 |

完整列表请查看 `.agent/workflows/` 目录。

---

## 🔧 使用 Hook 脚本

Hook 脚本需要手动运行（Antigravity 不支持自动触发）：

```bash
# 加载项目上下文
bash .agent/hooks/session-start.sh

# 提交前验证
bash .agent/hooks/validate-commit.sh

# 推送前检查
bash .agent/hooks/validate-push.sh

# 资产验证
bash .agent/hooks/validate-assets.sh

# 检测项目缺口
bash .agent/hooks/detect-gaps.sh
```

---

## 📏 编码规范

编码规范文档按代码类型组织，每个文件标注了适用路径：

| 规范文件 | 适用路径 |
|----------|----------|
| `gameplay-code.md` | `src/gameplay/**` |
| `engine-code.md` | `src/core/**` |
| `ai-code.md` | `src/ai/**` |
| `network-code.md` | `src/networking/**` |
| `ui-code.md` | `src/ui/**` |
| `design-docs.md` | `design/gdd/**` |
| `test-standards.md` | `tests/**` |
| `prototype-code.md` | `prototypes/**` |
| `shader-code.md` | shader 相关文件 |
| `narrative.md` | 叙事相关文件 |
| `data-files.md` | 数据文件 |

---

## 🚀 快速开始

1. 运行 `/start` 进入引导流程
2. 根据你的情况选择路径（无想法 / 有想法 / 有代码）
3. 系统会推荐下一步操作
