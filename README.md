<div align="center">

# Project Selfcheck

**Pre-commit Self-Review Tool for AI Coding Agents**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Agents Compatibility](https://img.shields.io/badge/Supported-Agents-blue)]()

A structured pre-commit review skill compatible with all AI coding agents.
It provides a four-stage verification workflow and supports dual interaction modes.

</div>

---

Navigation: [English](#english) | [中文文档](#中文文档)

---

<a id="english"></a>

## English

### What is it?
Project Selfcheck is a dedicated skill that guides AI coding agents to perform standardized pre-commit reviews.
Instead of committing code directly without inspection, the agent will run through four sequential phases and wait for your manual confirmation at every step.

### Workflow
```
Phase 1: Code Review
  → Detects code issues → Prompts you: "Fix these detected issues?"
  → After your confirmation → Proceed to Phase 2

Phase 2: Version Decision
  → Proposes new version tag vX.Y.Z.B → Prompts you: "Approve this version?"
  → After your confirmation → Proceed to Phase 3

Phase 3: Frontend Asset Sync
  → Scans files requiring synchronization → Prompts you: "Update these sync files?"
  → After your confirmation → Proceed to Phase 4

Phase 4: Changelog Update
  → Generates suggested changelog entries → Prompts you: "Commit this changelog?"
  → After your confirmation → Full self-check workflow completed
```

### Supported AI Agents
| Agent | Structured Q&A Support | Text Multi-turn Fallback |
|-------|:---:|:---:|
| TRAE | ✅ | ✅ |
| Claude Code | ✅ | ✅ |
| Cursor | ✅ | ✅ |
| GitHub Copilot | ❌ | ✅ |
| Cline / Roo Code | ❌ | ✅ |
| Aider | ❌ | ✅ |
| Windsurf | ❌ | ✅ |
| Augment | ❌ | ✅ |

> This skill automatically detects whether the target agent supports the `AskUserQuestion` interface.
> If supported, it uses structured interactive Q&A; if not, it falls back to plain text multi-turn dialogue, ensuring compatibility with **all mainstream AI coding agents**.

### Quick Start
#### Method 1: Let your AI agent complete the installation automatically
Copy the command below and send it to your coding agent:
```
Clone the GitHub repository /Motuo24/project-selfcheck, copy the entire project-selfcheck folder into your skills directory, and notify me once installation finishes.
```

#### Method 2: Manual Installation
Copy the entire `project-selfcheck/` directory into your agent's skills folder.

### How to Trigger
Send any of the following commands to your AI agent to launch the full self-check pipeline:
```
/project-selfcheck
code review
security audit
pre-commit check
```
The agent will automatically initialize the four-stage review pipeline.

### Core Features
- **Four-stage standard pipeline**: Code review, semantic version bump, frontend resource synchronization, changelog maintenance
- **Auto SemVer version increment**: Automatically judge major/minor/patch version based on modification scope, always increment build number B
- **Dual-mode interaction logic**: Native structured Q&A for agents with AskUserQuestion API, plain text fallback for others
- **Comprehensive security audit**: Scan hardcoded secrets, code injection vulnerabilities, access permission flaws
- **Pixel-perfect UI inspection**: Verify layout consistency, color matching, typography and interactive component states
- **Modular architecture**: Independent scene logic, standardized reference documents, reusable report templates

### File Structure
```
project-selfcheck/
├── SKILL.md                    # Skill entry file & scene routing controller
├── scenes/
│   ├── pre-commit.md           # Full pre-commit integrated review pipeline
│   ├── code-review.md          # Core code review (logic check, regression test, risk scan)
│   ├── ui-review.md            # Pixel-level UI & UX visual inspection
│   └── security-audit.md       # Specialized security audit (secrets, injection, auth validation)
├── references/
│   ├── core-constraints.md     # Dual interaction mode official protocol
│   ├── review-checklist.md     # Complete detailed review checklist
│   ├── version-decision.md     # SemVer bump rules + practical examples
│   └── reporting-standards.md  # Unified review report formatting rules
└── templates/
    ├── review-report/          # Standard review report template & demo fixtures
    └── version-bump/           # Version change record template & demo fixtures
```

---

<a id="中文文档"></a>

## 中文文档

### 这是什么？
Project Selfcheck 是一套面向 AI 编程助手的代码提交前结构化自查技能。
AI 不会直接提交代码，而是完整走完四段审查流程，每一步均暂停等待人工确认，规避各类线上问题。

### 工作流程
```
阶段一：代码审查
  → 扫描并列出代码隐患 → 询问："是否修复检测出的问题？"
  → 人工确认后 → 进入阶段二

阶段二：版本号判定
  → 生成建议版本号 vX.Y.Z.B → 询问："确认使用该版本号？"
  → 人工确认后 → 进入阶段三

阶段三：前端资源同步
  → 检索需要同步更新的静态文件 → 询问："是否同步更新以下文件？"
  → 人工确认后 → 进入阶段四

阶段四：更新日志维护
  → 生成变更日志草稿 → 询问："是否写入本次更新日志？"
  → 人工确认后 → 全套自查流程结束
```

### 兼容 AI 编程工具
| Agent | 结构化问答支持 | 纯文本多轮降级方案 |
|-------|:---:|:---:|
| TRAE | ✅ | ✅ |
| Claude Code | ✅ | ✅ |
| Cursor | ✅ | ✅ |
| GitHub Copilot | ❌ | ✅ |
| Cline / Roo Code | ❌ | ✅ |
| Aider | ❌ | ✅ |
| Windsurf | ❌ | ✅ |
| Augment | ❌ | ✅ |

> 技能会自动检测当前 AI 是否具备 `AskUserQuestion` 结构化交互接口。
> 支持接口则使用标准化弹窗问答；无接口自动降级为普通文字多轮对话，适配市面上**全部主流代码 AI 助手**。

### 快速安装
#### 方式一：交由 AI 自动部署
复制下方指令发送给你的编程助手完成一键安装：
```
克隆 GitHub 仓库 /Motuo24/project-selfcheck，将完整 project-selfcheck 文件夹复制到技能目录，安装完成后告知我。
```

#### 方式二：手动部署
直接将 `project-selfcheck/` 整个文件夹复制到对应 AI 的 skills 技能目录下即可。

### 使用触发指令
对 AI 发送任意一条指令，即可自动启动完整四段自查流水线：
```
/project-selfcheck
帮我自查一下
提交前检查
code review
安全检查
```

### 核心功能
- **四段式标准化流水线**：代码审查、语义版本升级、前端资源同步、更新日志生成
- **自动语义化版本迭代**：根据改动范围自动判断主/次/补丁版本，构建号 B 每次自增
- **双交互模式兼容**：有结构化接口则标准化问答，无接口自动切换普通对话
- **深度安全审计**：扫描硬编码密钥、注入漏洞、权限校验缺陷
- **像素级 UI 校验**：核对布局、配色、字体、组件交互状态还原度
- **模块化分层架构**：独立场景逻辑、配套规范文档、可复用报告模板

### 目录结构
```
project-selfcheck/
├── SKILL.md                    # 技能入口文件 + 场景路由控制器
├── scenes/
│   ├── pre-commit.md           # 完整提交前一体化审查流程
│   ├── code-review.md          # 代码核心审查（逻辑、回归、风险扫描）
│   ├── ui-review.md            # UI/UX 像素级视觉校验
│   └── security-audit.md       # 专项安全审计（密钥、注入、身份校验）
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

<p align="center">Released under MIT License · Built with ❤️</p>
