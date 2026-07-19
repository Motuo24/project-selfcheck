<div align="center">

# Project Selfcheck

**提交前自查自纠 · Pre-commit Self-Review Skill for AI Agents**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Agents](https://img.shields.io/badge/Agents-All-blue)]()

*一个兼容所有 AI 编程 Agent 的提交前审查技能，四阶段分步确认，双模式交互。*

</div>

---

Language: [English](#english) | [中文文档](#中文文档)

---

<a id="english"></a>

## English

### What is it?

Project Selfcheck is a skill that guides your AI coding agent through a structured pre-commit review. Instead of blindly committing, your agent will walk through four phases, pausing for your confirmation at each step.

### How it works

```
Phase 1: Code Review
  → Found issues → Asks you: "Fix these?"
  → You confirm  → Moves to Phase 2

Phase 2: Version Decision
  → Suggests vX.Y.Z.B → Asks you: "OK?"
  → You confirm       → Moves to Phase 3

Phase 3: Frontend Sync
  → Finds files to update → Asks you: "Update these?"
  → You confirm           → Moves to Phase 4

Phase 4: Changelog
  → Suggests changelog → Asks you: "Update?"
  → You confirm        → Done
```

### Supported Agents

| Agent | Structured Q&A | Multi-turn Fallback |
|-------|:---:|:---:|
| TRAE | ✅ | ✅ |
| Claude Code | ✅ | ✅ |
| Cursor | ✅ | ✅ |
| GitHub Copilot | ❌ | ✅ |
| Cline / Roo Code | ❌ | ✅ |
| Aider | ❌ | ✅ |
| Windsurf | ❌ | ✅ |
| Augment | ❌ | ✅ |

> The skill auto-detects whether the agent supports `AskUserQuestion`. If yes, it uses structured Q&A. If not, it falls back to plain-text multi-turn conversation — making it compatible with **all** AI coding agents.

### Quick Start

**Method 1: Let your agent install it for you**

Paste this into your agent:

```
Clone the project-selfcheck repo from GitHub, then copy the entire
project-selfcheck folder into my skills directory. Tell me when done.
```

**Method 2: Manual**

Copy the `project-selfcheck/` folder into your agent is skills directory.

### Usage

Just say any of these to your agent:

```
/project-selfcheck
帮我自查一下
提交前检查
code review
安全检查
```

Your agent will start the four-phase pipeline automatically.

### Features

- **Four-phase pipeline** — Code review, version bump, frontend sync, changelog
- **SemVer auto-bump** — Judges X/Y/Z from change type, B always increments
- **Dual-mode interaction** — Works with or without `AskUserQuestion`
- **Security audit** — Hardcoded secrets, injection risks, permission checks
- **UI review** — Pixel-level layout, color, typography, interaction states
- **Modular structure** — Scene routing, reference docs, reusable templates

### File Structure

```
project-selfcheck/
├── SKILL.md                    # Entry point + scene router
├── scenes/
│   ├── pre-commit.md           # Full pre-commit pipeline
│   ├── code-review.md          # Code review (security, logic, regression)
│   ├── ui-review.md            # UI/UX pixel-level check
│   └── security-audit.md       # Security audit (secrets, injection, auth)
├── references/
│   ├── core-constraints.md     # Dual-mode interaction protocol
│   ├── review-checklist.md     # Detailed review checklist
│   ├── version-decision.md     # Version bump rules + examples
│   └── reporting-standards.md  # Reporting guidelines
└── templates/
    ├── review-report/          # Review report template + fixture
    └── version-bump/           # Version bump template + fixture
```

---

<a id="中文文档"></a>

## 中文文档

### 这是什么？

Project Selfcheck 是一个让 AI 编程 Agent 在提交代码前进行结构化自查的技能。Agent 不会直接提交，而是经过四个阶段、每阶段停下来等你确认，确保没有遗漏。

### 工作流程

```
阶段一：代码审查
  → 发现问题 → 问你："需要修复吗？"
  → 你确认   → 进入阶段二

阶段二：版本号决策
  → 建议 vX.Y.Z.B → 问你："可以吗？"
  → 你确认       → 进入阶段三

阶段三：前端同步
  → 找到需同步的文件 → 问你："更新这些？"
  → 你确认         → 进入阶段四

阶段四：更新日志
  → 建议更新内容 → 问你："更新吗？"
  → 你确认      → 完成
```

### 适配 Agent

| Agent | 结构化 Q&A | 多轮对话降级 |
|-------|:---:|:---:|
| TRAE | ✅ | ✅ |
| Claude Code | ✅ | ✅ |
| Cursor | ✅ | ✅ |
| GitHub Copilot | ❌ | ✅ |
| Cline / Roo Code | ❌ | ✅ |
| Aider | ❌ | ✅ |
| Windsurf | ❌ | ✅ |
| Augment | ❌ | ✅ |

> Skill 会自动检测 Agent 是否支持 `AskUserQuestion`。支持就用结构化 Q&A，不支持就降级为纯文本多轮对话，兼容**所有** AI 编程 Agent。

### 快速开始

**方式一：让 Agent 帮你装**

把这句话发给你的 Agent：

```
把 /Motuo24/project-selfcheck 仓库从 GitHub 克隆下来，将整个 project-selfcheck
文件夹复制到我的 skills 目录里，装好后告诉我一声。
```

**方式二：手动安装**

将 `project-selfcheck/` 文件夹复制到你的 Agent 技能目录。

### 使用方式

对你的 Agent 说以下任意一句：

```
/project-selfcheck
帮我自查一下
提交前检查
code review
安全检查
```

Agent 会自动启动四阶段审查流水线。

### 特性

- **四阶段流水线** — 代码审查、版本号变更、前端同步、更新日志
- **SemVer 自动变更** — 根据变更类型判断 X/Y/Z，B 号始终递增
- **双模式交互** — 有 `AskUserQuestion` 用结构化 Q&A，没有就多轮对话
- **安全审计** — 硬编码密钥、注入风险、权限校验
- **UI 还原度** — 像素级布局、颜色、排版、交互状态
- **模块化设计** — 场景路由、参考文档、可复用模板

### 文件结构

```
project-selfcheck/
├── SKILL.md                    # 入口 + 场景路由
├── scenes/
│   ├── pre-commit.md           # 提交前全面自查
│   ├── code-review.md          # 代码审查（安全、逻辑、回归）
│   ├── ui-review.md            # UI/UX 像素级检查
│   └── security-audit.md       # 安全审计（密钥、注入、认证）
├── references/
│   ├── core-constraints.md     # 双模式交互协议
│   ├── review-checklist.md     # 详细审查清单
│   ├── version-decision.md     # 版本号决策规则 + 示例
│   └── reporting-standards.md  # 汇报规范
└── templates/
    ├── review-report/          # 审查报告模板 + 示例数据
    └── version-bump/           # 版本变更模板 + 示例数据
```

---

<p align="center">MIT License · Made with ❤️</p>