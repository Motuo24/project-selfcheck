# Project Selfcheck

> 提交前自查自纠 Skill — 支持所有 AI Agent，双模式交互

[English](#english) | [中文](#chinese)

---

<a id="english"></a>

## English

### What is Project Selfcheck?

A pre-commit self-review skill for AI coding agents. It guides the agent through a structured four-phase review process before every commit:

1. **Code Review** — Requirements compliance, logic bugs, edge cases, regression
2. **Version Decision** — Auto-suggest version bump based on SemVer + build number
3. **Frontend Sync** — Identify files that need version number updates
4. **Changelog** — Update release notes and update history

### Supported Agents

| Agent | AskUserQuestion | Multi-turn Text | Notes |
|-------|:---:|:---:|-------|
| **TRAE** | ✅ | ✅ | Full support, native AskUserQuestion |
| **Claude Code** | ✅ | ✅ | Full support |
| **Cursor** | ✅ | ✅ | Full support |
| **GitHub Copilot** | ❌ | ✅ | Falls back to multi-turn text |
| **Cline** | ❌ | ✅ | Falls back to multi-turn text |
| **Aider** | ❌ | ✅ | Falls back to multi-turn text |
| **Any Agent** | ✅/❌ | ✅ | Universal multi-turn fallback |

> **Dual-Mode Interaction**: The skill auto-detects whether the agent supports `AskUserQuestion`. If yes, it uses structured Q&A with options. If not, it falls back to plain-text multi-turn conversation — making it compatible with **all** AI coding agents.

### Features

- **Four-phase review pipeline** with mandatory user confirmation between each phase
- **Automatic version bump**: Judges X/Y/Z based on change type, B always increments
- **Dual-mode interaction**: Structured Q&A or plain-text multi-turn, auto-detected
- **Modular structure**: Scene routing, reference docs, reusable templates
- **Security-first**: Hardcoded secrets, injection risks, permission checks
- **UI review**: Pixel-level layout, color, typography, and interaction checks

### Installation

**Method 1: Let your Agent do it (recommended)**

Copy the repo URL and paste this into your Agent:

```
Clone the project-selfcheck repo from GitHub, then copy the entire project-selfcheck folder into my skills directory. After that, tell me it is ready to use.
```

Or even simpler:

```
Install the project-selfcheck skill from <repo-url> for me.
```

Your Agent will clone the repo, find the correct skills directory, copy the files, and confirm everything is set up. No manual steps needed.

**Method 2: Manual install**

Copy the entire `project-selfcheck` folder into your agent is skills directory:

```
<skills-root>/
└── project-selfcheck/
    ├── SKILL.md
    ├── scenes/
    │   ├── pre-commit.md
    │   ├── code-review.md
    │   ├── ui-review.md
    │   └── security-audit.md
    ├── references/
    │   ├── core-constraints.md
    │   ├── review-checklist.md
    │   ├── version-decision.md
    │   └── reporting-standards.md
    └── templates/
        ├── manifest.json
        ├── review-report/
        └── version-bump/
```

### Usage

Trigger the skill with any of these commands:

```
/project-selfcheck
帮我自查一下
提交前检查
code review
安全检查
```

The agent will then run through the four-phase pipeline, pausing for your confirmation at each step.

---

<a id="chinese"></a>

## 中文

### 什么是 Project Selfcheck？

一个面向 AI 编程 Agent 的提交前自查自纠技能。它引导 Agent 在每次提交前完成四个阶段的结构化审查：

1. **代码审查** — 需求符合度、逻辑 Bug、边界条件、回归风险
2. **版本号决策** — 基于 SemVer 自动判断版本号变更
3. **前端同步** — 识别需要同步版本号的文件
4. **更新日志** — 更新发布说明和历史记录

### 适配 Agent

| Agent | 结构化提问 | 多轮对话 | 说明 |
|-------|:---:|:---:|-------|
| **TRAE** | ✅ | ✅ | 完整支持，原生 AskUserQuestion |
| **Claude Code** | ✅ | ✅ | 完整支持 |
| **Cursor** | ✅ | ✅ | 完整支持 |
| **GitHub Copilot** | ❌ | ✅ | 降级为多轮文本对话 |
| **Cline** | ❌ | ✅ | 降级为多轮文本对话 |
| **Aider** | ❌ | ✅ | 降级为多轮文本对话 |
| **任意 Agent** | ✅/❌ | ✅ | 通用多轮对话兜底 |

> **双模式交互**：Skill 自动检测 Agent 是否支持 `AskUserQuestion` 工具。支持时使用结构化 Q&A 带选项，不支持时降级为纯文本多轮对话 — 兼容**所有** AI 编程 Agent。

### 特性

- **四阶段审查流水线**，每阶段之间强制等待用户确认
- **自动版本号变更**：根据变更类型判断 X/Y/Z，B 号始终递增
- **双模式交互**：结构化 Q&A 或纯文本多轮对话，自动检测切换
- **模块化结构**：场景路由、参考文档、可复用模板
- **安全优先**：硬编码密钥、注入风险、权限校验
- **UI 还原度检查**：像素级布局、颜色、排版、交互状态

### 安装

**方式一：让 Agent 帮你装（推荐）**

把仓库地址发给你的 Agent，一句话搞定：

```
把 project-selfcheck 仓库从 GitHub 克隆下来，然后将整个 project-selfcheck 文件夹复制到我的 skills 目录里，装好后告诉我一声。
```

你的 Agent 会自动完成克隆 → 定位目录 → 复制文件 → 确认安装，全程无需手动操作。

**方式二：手动安装**

将整个 `project-selfcheck` 文件夹复制到你的 Agent 技能目录：

```
<skills-root>/
└── project-selfcheck/
    ├── SKILL.md
    ├── scenes/
    │   ├── pre-commit.md
    │   ├── code-review.md
    │   ├── ui-review.md
    │   └── security-audit.md
    ├── references/
    │   ├── core-constraints.md
    │   ├── review-checklist.md
    │   ├── version-decision.md
    │   └── reporting-standards.md
    └── templates/
        ├── manifest.json
        ├── review-report/
        └── version-bump/
```

### 使用方式

通过以下任一指令触发：

```
/project-selfcheck
帮我自查一下
提交前检查
code review
安全检查
```

Agent 将按四阶段流水线执行，每个阶段结束后暂停等待你确认。

---

## License

MIT