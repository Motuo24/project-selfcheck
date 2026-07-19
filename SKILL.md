---
name: project-selfcheck
description: "提交前自查自纠：检查需求符合度、代码隐患、UI还原度、安全风险，并决策版本号。当用户触发 /project-selfcheck 指令、要求代码审查或提交前检查时调用。"
user-invocable: true
disable-model-invocation: false
---

# 项目自查自纠

## 范围

当用户准备提交代码、需要代码审查、或明确要求自查自纠时使用本 Skill。覆盖五个维度：需求符合度、代码质量、UI/UX 还原度、安全风险、版本号决策。

不适用于：日常编码过程中的临时检查、单文件快速浏览、或用户未明确要求审查的场景。

## 文件地图

`{{SKILL_DIR}}` 指本 `SKILL.md` 所在目录。

```
{{SKILL_DIR}}/
├── SKILL.md                       ← 总入口（本文件）
├── scenes/                        ← 场景级指导（按用户意图路由）
│   ├── pre-commit.md              ← 提交前全面自查
│   ├── code-review.md             ← 代码审查专项
│   ├── ui-review.md               ← UI/UX 还原度检查
│   └── security-audit.md          ← 安全审计
├── references/                    ← 参考文档
│   ├── review-checklist.md        ← 详细审查清单
│   ├── version-decision.md        ← 版本号决策规则
│   ├── reporting-standards.md     ← 汇报规范
│   └── core-constraints.md        ← 核心约束（含双模式交互协议）
└── templates/                     ← 可复用模板
    ├── manifest.json
    ├── review-report/
    │   ├── template.md            ← 审查报告模板说明
    │   └── fixture.json           ← 示例数据
    └── version-bump/
        ├── template.md            ← 版本号变更模板说明
        └── fixture.json           ← 示例数据
```

## 场景路由

读取用户意图，路由到对应场景文件：

| 用户意图 | 场景文件 | 说明 |
|---------|---------|------|
| 提交前全面检查、/project-selfcheck 指令 | `scenes/pre-commit.md` | 默认入口，覆盖全部维度 |
| 纯代码审查、检查逻辑/bug/异常处理 | `scenes/code-review.md` | 聚焦代码质量 |
| UI/UX 还原度、对照设计稿检查 | `scenes/ui-review.md` | 聚焦视觉还原 |
| 安全专项审计、密钥/注入/权限 | `scenes/security-audit.md` | 聚焦安全风险 |

工作流：
1. 根据用户意图路由到对应场景文件。
2. 场景文件会引用 `references/` 下的详细清单和规则。
3. 汇报时参考 `references/reporting-standards.md` 的规范。
4. 版本决策时参考 `references/version-decision.md` 的规则。
5. 整个过程遵守 `references/core-constraints.md` 的约束。

## 核心协议

所有场景共享以下协议：

**审查维度**：安全（密钥/注入/权限）→ 逻辑（空值/边界/异步/异常）→ 回归（稳定性）→ 需求符合度 → UI 还原度（如涉及）。

**用户交互**：必须遵守 `references/core-constraints.md` 中的「用户交互协议（双模式）」。支持 `AskUserQuestion` 工具时使用结构化提问，不支持时使用纯文本多轮对话。每次只抛一个议题，等用户回复后再继续。

**协作原则**：发现问题 → 列出事实（位置、现象、风险）→ 请示决策 → 等待指令。每次只处理一个核心议题，获得明确指令前绝不修改代码。

**汇报风格**：先给结论，再谈关键问题，最后简述改动。像资深工程师做 Code Review。兜底：若审查通过，回复「自查通过，符合提交标准」并附带版本号。

详细规则见 `references/` 下各文档。