<div align="center">

# Project Selfcheck

**Pre-commit Self-Review Tool for AI Coding Agents**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Supported Agents](https://img.shields.io/badge/Supported-Agents-blue.svg)](#compatibility-table)

A structured pre-commit review skill compatible with all mainstream AI coding agents.
It provides a standardized four-stage verification workflow and supports dual interaction fallback modes.

</div>

---

## Table of Contents
- [Project Selfcheck](#project-selfcheck)
  - [Table of Contents](#table-of-contents)
- [English Documentation](#english-documentation)
  - [What is it?](#what-is-it)
  - [Core Workflow](#core-workflow)
  - [Supported AI Agents Compatibility](#supported-ai-agents-compatibility)
  - [Quick Start Installation](#quick-start-installation)
    - [Method 1: Auto Installation via AI Agent](#method-1-auto-installation-via-ai-agent)
    - [Method 2: Manual Installation](#method-2-manual-installation)
  - [Trigger Commands (All cross-language compatible)](#trigger-commands-all-cross-language-compatible)
  - [Core Features](#core-features)
  - [Project File Structure](#project-file-structure)
- [中文文档](#中文文档)
  - [工具介绍](#工具介绍)
  - [完整工作流程](#完整工作流程)
  - [兼容 AI 编程工具列表](#兼容-ai-编程工具列表)
  - [快速安装教程](#快速安装教程)
    - [方式一：交由 AI 自动部署](#方式一交由-ai-自动部署)
    - [方式二：手动部署](#方式二手动部署)
  - [全局触发指令（中英文互通）](#全局触发指令中英文互通)
  - [核心功能](#核心功能)
  - [项目目录结构](#项目目录结构)
- [FAQ 常见问题](#faq-常见问题)
    - [Q1：各个 AI 工具的 skills 文件夹存放路径？](#q1各个-ai-工具的-skills-文件夹存放路径)
    - [Q2：AI 只返回文字，不弹出结构化确认弹窗？](#q2ai-只返回文字不弹出结构化确认弹窗)
    - [Q3：拒绝某一步检查后如何重新运行自查？](#q3拒绝某一步检查后如何重新运行自查)
    - [Q4：如何更新/卸载本技能？](#q4如何更新卸载本技能)
    - [Q5：支持哪些编程语言代码审计？](#q5支持哪些编程语言代码审计)
- [License](#license)

---

<a id="english-docs"></a>
# English Documentation

<a id="what-is-it"></a>
## What is it?
Project Selfcheck is a dedicated skill that guides AI coding agents to perform standardized pre-commit reviews.
Instead of committing uninspected code directly, the agent runs through four sequential phases, pausing for manual user confirmation at every single stage to avoid security risks, inconsistent versions, missing sync assets and empty changelogs.

<a id="core-workflow"></a>
## Core Workflow
```text
Phase 1: Code Review
  → Detects code logic bugs, regressions & security risks → Prompt: "Fix these detected issues?"
  → Proceed to Phase 2 after user confirmation

Phase 2: Version Decision
  → Auto-generate candidate SemVer tag vX.Y.Z.B → Prompt: "Approve this version tag?"
  → Proceed to Phase 3 after user confirmation

Phase 3: Frontend Asset Sync
  → Scan static files requiring synchronization → Prompt: "Update these sync files?"
  → Proceed to Phase 4 after user confirmation

Phase 4: Changelog Update
  → Generate formatted changelog draft → Prompt: "Commit this changelog entry?"
  → Full self-check pipeline completed
```
> Pipeline Rule: If you reject any step, the entire self-check workflow will terminate immediately for code adjustment.

<a id="compatibility-table"></a>
## Supported AI Agents Compatibility
| Agent | Structured AskUserQuestion Q&A | Plain Text Multi-turn Fallback |
|-------|:---:|:---:|
| TRAE | ✅ | ✅ |
| Claude Code | ✅ | ✅ |
| Cursor | ✅ | ✅ |
| WorkBuddy | ✅ | ✅ |
| Codex | ✅ | ✅ |
| QwenPAW | ✅ | ✅ |
| GitHub Copilot | ❌ | ✅ |
| Cline / Roo Code | ❌ | ✅ |
| Aider | ❌ | ✅ |
| Windsurf | ❌ | ✅ |
| Augment | ❌ | ✅ |
| OpenClaw | ❌ | ✅ |

This skill auto-detects whether your AI agent supports the `AskUserQuestion` native interactive interface:
1. If supported: Use standardized structured pop-up questions
2. If unsupported: Automatically fallback to plain text multi-turn dialogue
Guarantees compatibility with all mainstream AI coding assistants.

<a id="quick-start-install"></a>
## Quick Start Installation
### Method 1: Auto Installation via AI Agent
Copy the below shell instruction and send it to your coding agent for one-click deployment:
```shell
# Clone repo and deploy skill folder
git clone https://github.com/Motuo24/project-selfcheck.git
Copy the entire project-selfcheck folder into your agent's skills directory, notify me once finished.
```

### Method 2: Manual Installation
1. Clone this repository locally
2. Copy the whole `project-selfcheck/` directory into your AI agent's `skills` folder

> Reference: Different agents have different skills storage paths, check FAQ section for details.

<a id="trigger-commands-en"></a>
## Trigger Commands (All cross-language compatible)
Send any of the below commands to your AI agent to launch the full 4-stage self-check pipeline:
```text
/project-selfcheck
code review
security audit
pre-commit check
```
Chinese trigger phrases also work for agents with Chinese language context.

<a id="core-features"></a>
## Core Features
1. **Standard 4-stage pipeline**: Code review, semantic version bump, frontend static asset sync, changelog maintenance
2. **Auto SemVer vX.Y.Z.B increment logic**:
   - X: Major breaking change
   - Y: Minor new feature
   - Z: Patch bug fix
   - B: Build number, increments on every self-check run
3. **Dual interaction mode**: Native structured Q&A for supported agents, text fallback for others
4. **Full security audit**: Scan hardcoded secrets, SQL/script injection vulnerabilities, permission validation defects
5. **Pixel-level UI inspection**: Check layout consistency, color scheme, typography and interactive component states
6. **Modular decoupled architecture**: Independent scene logic, standardized spec docs, reusable report templates

<a id="file-structure"></a>
## Project File Structure
```tree
project-selfcheck/
├── SKILL.md                    # Skill entry file & scene routing controller
├── scenes/
│   ├── pre-commit.md           # Full integrated pre-commit review pipeline
│   ├── code-review.md          # Core logic, regression & risk scanning rules
│   ├── ui-review.md            # Pixel-level UI & UX visual inspection rules
│   └── security-audit.md       # Specialized secret & injection audit rules
├── references/
│   ├── core-constraints.md     # Dual interaction mode official protocol spec
│   ├── review-checklist.md     # Complete full review item checklist
│   ├── version-decision.md     # SemVer bump rules + real world examples
│   └── reporting-standards.md  # Unified review report output format rules
└── templates/
    ├── review-report/          # Standard review report template & demo fixtures
    └── version-bump/           # Version change record template & demo fixtures
```

---

<a id="zh-docs"></a>
# 中文文档

<a id="intro-cn"></a>
## 工具介绍
Project Selfcheck 是一套面向 AI 编程助手的提交前结构化自查技能。
AI 不会直接提交未经校验的代码，会完整执行四段标准化审查流程，每一步均暂停等待人工确认；若否决任意环节则直接终止流程修改代码，从源头规避线上漏洞、版本混乱、静态资源漏同步、更新日志缺失等问题。

<a id="workflow-cn"></a>
## 完整工作流程
```text
阶段一：代码审查
  → 扫描逻辑缺陷、回归问题、安全隐患 → 询问："是否修复检测出的问题？"
  → 人工确认后进入阶段二

阶段二：版本号判定
  → 自动生成四段式语义版本 vX.Y.Z.B → 询问："确认使用该版本号？"
  → 人工确认后进入阶段三

阶段三：前端资源同步
  → 检索需同步更新的静态资源文件 → 询问："是否同步更新以下文件？"
  → 人工确认后进入阶段四

阶段四：更新日志维护
  → 生成标准化变更日志草稿 → 询问："是否写入本次更新日志？"
  → 全套自查流程执行完毕
```
> 流程规则：任意步骤选择「否」，将直接终止全部自查流水线，返回代码修改环节。

<a id="compatibility-table-cn"></a>
## 兼容 AI 编程工具列表
| 工具名称 | 结构化 AskUserQuestion 问答 | 纯文本多轮降级方案 |
|-------|:---:|:---:|
| TRAE | ✅ | ✅ |
| Claude Code | ✅ | ✅ |
| Cursor | ✅ | ✅ |
| WorkBuddy | ✅ | ✅ |
| Codex | ✅ | ✅ |
| QwenPAW | ✅ | ✅ |
| GitHub Copilot | ❌ | ✅ |
| Cline / Roo Code | ❌ | ✅ |
| Aider | ❌ | ✅ |
| Windsurf | ❌ | ✅ |
| Augment | ❌ | ✅ |
| OpenClaw | ❌ | ✅ |

技能会自动检测当前 AI 是否具备 `AskUserQuestion` 原生结构化交互接口：
1. 支持接口：使用标准化弹窗问答交互
2. 无接口：自动降级为普通文字多轮对话
完全适配市面所有主流代码 AI 助手。

<a id="install-cn"></a>
## 快速安装教程
### 方式一：交由 AI 自动部署
复制下方指令发送给编程助手一键完成克隆与部署：
```shell
git clone https://github.com/Motuo24/project-selfcheck.git
将完整 project-selfcheck 文件夹复制到技能目录，部署完成后告知我。
```

### 方式二：手动部署
1. 本地克隆本仓库
2. 将 `project-selfcheck/` 整个文件夹复制到对应 AI 的 skills 技能目录

> 不同客户端技能存放路径不一致，具体查看下方 FAQ 板块。

<a id="trigger-cn"></a>
## 全局触发指令（中英文互通）
向 AI 发送任意一条指令，即可启动完整四段自查流水线：
```text
/project-selfcheck
code review
安全检查
提交前检查
帮我自查一下
```

<a id="features-cn"></a>
## 核心功能
1. **四段式标准化流水线**：代码审查、语义版本升级、前端静态资源同步、更新日志自动生成
2. **四段式语义化版本自动迭代 vX.Y.Z.B**
   - X：不兼容破坏性大版本更新
   - Y：新增功能次版本
   - Z：Bug 修复补丁版本
   - B：构建号，每次执行自查自动自增
3. **双交互模式兼容逻辑**：支持原生结构化问答，无接口自动切换普通对话
4. **深度安全审计**：扫描硬编码密钥、注入漏洞、权限校验缺失问题
5. **像素级 UI 视觉校验**：核对页面布局、配色、字体、交互组件展示一致性
6. **模块化分层架构**：场景逻辑解耦、配套完整规范文档、可复用标准化报告模板

<a id="dir-cn"></a>
## 项目目录结构
```tree
project-selfcheck/
├── SKILL.md                    # 技能入口文件 + 场景路由控制器
├── scenes/
│   ├── pre-commit.md           # 完整提交前一体化审查流程
│   ├── code-review.md          # 代码核心审查（逻辑、回归、风险扫描规则）
│   ├── ui-review.md            # UI/UX 像素级视觉校验规则
│   └── security-audit.md       # 专项安全审计（密钥、注入、身份校验规则）
├── references/
│   ├── core-constraints.md     # 双交互模式协议规范
│   ├── review-checklist.md     # 完整详细审查清单
│   ├── version-decision.md     # 版本迭代规则 + 实操示例
│   └── reporting-standards.md  # 统一审查报告输出规范
└── templates/
    ├── review-report/          # 审查报告标准模板 + 示例数据
    └── version-bump/           # 版本变更记录模板 + 示例数据
```

---

<a id="faq"></a>
# FAQ 常见问题
### Q1：各个 AI 工具的 skills 文件夹存放路径？
所有 AI Agent 都具备修改自身工作区目录的能力，无需手动查找路径。只需将上文的安装指令复制给你的 Agent，即可自动完成克隆和部署。

### Q2：AI 只返回文字，不弹出结构化确认弹窗？
当前 Agent 不支持 AskUserQuestion 接口，工具会自动降级为文本对话，不影响完整自查流程。

### Q3：拒绝某一步检查后如何重新运行自查？
修改对应代码/资源后，重新输入任意一条触发指令重启完整流水线。

### Q4：如何更新/卸载本技能？
- 更新：重新克隆仓库覆盖原 project-selfcheck 文件夹
- 卸载：直接删除对应 skills 目录下的 project-selfcheck 文件夹

### Q5：支持哪些编程语言代码审计？
支持所有编程语言。本技能进行的是通用代码逻辑审查、安全风险扫描和版本管理，与具体编程语言无关。

---

<a id="license-info"></a>
# License
This project is released under the [MIT License](./LICENSE).
You are free to use, modify and distribute this project for commercial and non-commercial purposes.

<p align="center">Released under MIT License · Built with ❤️</p>