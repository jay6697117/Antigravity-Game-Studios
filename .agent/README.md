# Antigravity Game Studios — 完整使用指南

> 从 Claude Code Game Studios 适配而来的 AI 游戏开发团队系统
> **48 个 Agent** · **45 个工作流** · **8 个 Hook 脚本** · **11 个编码规范** · **29 个文档模板**

---

## 📂 目录结构

```
.agent/
├── README.md                # 本文件
├── settings-reference.md    # 安全与权限参考
├── statusline.sh            # 状态栏脚本
├── agents/      (48 文件)    # Agent 角色定义
├── workflows/   (45 文件)    # 工作流（斜杠命令）
├── hooks/       (8 文件)     # 自动化脚本（原始 bash）
├── rules/       (11 文件)    # 编码规范
└── docs/                    # 参考文档与模板
    ├── (15 个参考文档)
    ├── templates/  (29 文件)  # 文档模板
    └── hooks-reference/ (6 文件) # Hook 详细参考
```

---

## 🤖 Agent 角色（48 个）

Agent 定义了各职位的职责、决策框架和协作协议。查阅文件路径：`.agent/agents/[name].md`

### 第一层 — 总监（3 个）

| Agent | 说明 |
|-------|------|
| `creative-director` | 创意总监 — 游戏愿景、支柱决策、跨部门冲突仲裁 |
| `technical-director` | 技术总监 — 技术架构、性能标准、技术债务 |
| `producer` | 制作人 — 跨部门协调、冲刺计划、里程碑管理 |

### 第二层 — 部门主管（8 个）

| Agent | 说明 |
|-------|------|
| `game-designer` | 游戏设计主管 — 机制设计、系统平衡 |
| `lead-programmer` | 首席程序员 — 代码架构、接口设计 |
| `art-director` | 美术总监 — 视觉风格、资产标准 |
| `audio-director` | 音频总监 — 音效方向、音乐风格 |
| `narrative-director` | 叙事总监 — 故事架构、角色发展 |
| `qa-lead` | QA 主管 — 测试策略、Bug 分类 |
| `release-manager` | 发布经理 — 发布流程、版本管理 |
| `localization-lead` | 本地化主管 — 多语言策略、翻译管理 |

### 第三层 — 专家（37 个）

| 领域 | Agent |
|------|-------|
| **程序** | `gameplay-programmer` `engine-programmer` `ai-programmer` `network-programmer` `ui-programmer` `tools-programmer` |
| **设计** | `systems-designer` `level-designer` `economy-designer` `ux-designer` |
| **美术/音频** | `technical-artist` `sound-designer` |
| **叙事** | `writer` `world-builder` |
| **QA/运维** | `qa-tester` `performance-analyst` `devops-engineer` `security-engineer` `accessibility-specialist` `analytics-engineer` |
| **运营** | `live-ops-designer` `community-manager` `prototyper` |
| **Godot** | `godot-specialist` `godot-gdscript-specialist` `godot-shader-specialist` `godot-gdextension-specialist` |
| **Unity** | `unity-specialist` `unity-dots-specialist` `unity-shader-specialist` `unity-addressables-specialist` `unity-ui-specialist` |
| **Unreal** | `unreal-specialist` `ue-gas-specialist` `ue-blueprint-specialist` `ue-replication-specialist` `ue-umg-specialist` |

### 使用方式

在对话中提到对应角色名即可获取专业指导，例如：
- "以 `creative-director` 的视角审查这个游戏概念"
- "按照 `gameplay-programmer` 的规范实现这个系统"

---

## ⚡ 工作流（45 个斜杠命令）

在对话中输入 `/命令名` 触发。文件路径：`.agent/workflows/[name].md`

### 入门与项目管理

| 命令 | 说明 |
|------|------|
| `/start` | 引导式新手流程 — 根据你的状态推荐下一步 |
| `/project-stage-detect` | 自动分析项目阶段、识别缺口 |
| `/onboard` | 生成新成员入职文档 |
| `/setup-engine` | 配置游戏引擎和版本 |

### 创意与设计

| 命令 | 说明 |
|------|------|
| `/brainstorm` | 游戏概念头脑风暴（MDA 框架、玩家心理） |
| `/map-systems` | 拆解游戏概念为系统、映射依赖 |
| `/design-system` | 逐章节引导撰写 GDD |
| `/design-review` | 设计文档完整性和一致性审查 |
| `/prototype` | 快速原型制作（跳过标准流程） |
| `/playtest-report` | 生成或分析测试报告 |

### 代码审查与质量

| 命令 | 说明 |
|------|------|
| `/code-review` | 架构和代码质量审查 |
| `/balance-check` | 游戏平衡性分析（公式、经济） |
| `/asset-audit` | 资产命名、大小、格式合规检查 |
| `/perf-profile` | 性能瓶颈分析和优化建议 |
| `/tech-debt` | 技术债务追踪和优先级排序 |
| `/scope-check` | 范围蔓延检测 |

### 生产管理

| 命令 | 说明 |
|------|------|
| `/sprint-plan` | 冲刺计划制定或更新 |
| `/milestone-review` | 里程碑进度审查 |
| `/estimate` | 任务工作量估算 |
| `/retrospective` | 回顾总结（速度、阻碍、模式） |
| `/bug-report` | 结构化 Bug 报告 |
| `/gate-check` | 阶段门禁验证 |
| `/architecture-decision` | 架构决策记录（ADR） |

### 发布与运维

| 命令 | 说明 |
|------|------|
| `/release-checklist` | 发布前验证清单 |
| `/launch-checklist` | 上线准备验证（全部门） |
| `/changelog` | 从 Git 生成变更日志 |
| `/patch-notes` | 生成面向玩家的更新说明 |
| `/hotfix` | 紧急修复工作流 |
| `/localize` | 本地化工作流 |
| `/reverse-document` | 从代码反向生成设计文档 |

### 团队协调（多角色联动）

| 命令 | 说明 |
|------|------|
| `/team-combat` | 协调战斗系统：设计→编程→AI→QA |
| `/team-narrative` | 协调叙事团队：编剧→世界观→关卡 |
| `/team-ui` | 协调 UI 团队：UX→编程→美术 |
| `/team-release` | 协调发布团队：QA→DevOps→制作人 |
| `/team-polish` | 协调打磨团队：性能→美术→音效→QA |
| `/team-audio` | 协调音频团队：方向→设计→技术→实现 |
| `/team-level` | 协调关卡团队：设计→叙事→美术→QA |

### Hook 工作流（自动化检查）

| 命令 | 说明 |
|------|------|
| `/session-context` | 开始工作时加载项目上下文 |
| `/session-end` | 结束工作时记录会话日志 |
| `/save-state` | 保存当前工作状态防丢失 |
| `/validate-commit` | 提交前检查代码质量 |
| `/validate-push` | 推送前检查受保护分支 |
| `/validate-assets` | 验证资产命名和 JSON |
| `/detect-gaps` | 检测代码与文档的差距 |
| `/log-agent` | 记录 Agent 调用审计日志 |

---

## 📏 编码规范（11 个）

当修改特定路径的代码时，参考对应规范。文件路径：`.agent/rules/[name].md`

| 规范 | 适用路径 | 核心要求 |
|------|----------|----------|
| `gameplay-code` | `src/gameplay/**` | 数据驱动、delta time、无 UI 引用 |
| `engine-code` | `src/core/**` | 零分配热路径、线程安全、API 稳定 |
| `ai-code` | `src/ai/**` | 性能预算、可调试性、数据驱动参数 |
| `network-code` | `src/networking/**` | 服务器权威、版本化消息、安全 |
| `ui-code` | `src/ui/**` | 无游戏状态持有、本地化就绪、无障碍 |
| `design-docs` | `design/gdd/**` | 必需 8 个章节、公式格式、边界情况 |
| `test-standards` | `tests/**` | 测试命名、覆盖率、fixture 模式 |
| `prototype-code` | `prototypes/**` | 宽松标准、需 README、记录假设 |
| `shader-code` | shader 文件 | Shader 编码规范 |
| `narrative` | 叙事文件 | 叙事内容格式规范 |
| `data-files` | 数据文件 | 数据文件格式约定 |

---

## 📚 参考文档与模板

### 参考文档（`.agent/docs/`）

| 文档 | 说明 |
|------|------|
| `quick-start.md` | 详细使用指南 |
| `agent-roster.md` | Agent 完整名册表 |
| `agent-coordination-map.md` | Agent 委托与升级路径图 |
| `coordination-rules.md` | 协调规则 |
| `coding-standards.md` | 编码标准概述 |
| `technical-preferences.md` | 技术偏好（引擎、语言等） |
| `directory-structure.md` | 项目目录结构说明 |
| `context-management.md` | 上下文管理策略 |
| `setup-requirements.md` | 环境要求和平台说明 |
| `skills-reference.md` | Skill 命令参考 |
| `hooks-reference.md` | Hook 脚本参考 |
| `rules-reference.md` | Rule 规范参考 |
| `review-workflow.md` | 审查工作流 |
| `CLAUDE-local-template.md` | 本地配置模板 |
| `settings-local-template.md` | 本地设置模板 |

### 文档模板（`.agent/docs/templates/`）

29 个开箱即用的文档模板，涵盖：

| 类别 | 模板 |
|------|------|
| **设计** | `game-concept` `game-design-document` `game-pillars` `level-design-document` `faction-design` `economy-model` `systems-index` |
| **技术** | `technical-design-document` `architecture-decision-record` |
| **叙事** | `narrative-character-sheet` |
| **美术/音频** | `art-bible` `sound-bible` |
| **生产** | `sprint-plan` `milestone-definition` `pitch-document` `release-notes` `release-checklist-template` `changelog-template` `risk-register-entry` |
| **QA** | `test-plan` `incident-response` `post-mortem` |
| **报告** | `project-stage-report` `playtest-report` |
| **逆向** | `architecture-doc-from-code` `concept-doc-from-prototype` `design-doc-from-implementation` |
| **协作** | `collaborative-protocols/` 下 3 个协议模板 |

---

## 🔒 安全参考

详见 `.agent/settings-reference.md`：
- ✅ 安全操作列表（git status、pytest 等可放心执行）
- 🚫 危险操作列表（rm -rf、force push 等需谨慎）
- 🔒 受保护文件列表（.env 等禁止读写）

---

## 🚀 快速开始

1. **首次使用** → 运行 `/start`，系统会引导你选择路径
2. **每次开始工作** → 运行 `/session-context` 加载项目上下文
3. **提交代码前** → 运行 `/validate-commit` 检查质量
4. **结束工作时** → 运行 `/session-end` 记录工作日志
