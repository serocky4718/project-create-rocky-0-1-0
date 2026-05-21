---
name: project-create-rocky-0-1-0
description: Rocky 版中文通用项目创建规则。用于新项目启动、PM 需求探讨、项目规模判断、PRD/TASKS/HANDOFF 等文件生成、README 角色入口、职位提示词、手动跨窗口交接、验证命令、回滚策略，以及 PRD 后 GitHub 自动建库。
---

# Project Create Rocky 0.1.0

这是一个“项目创建与角色协作”的路由型 skill。

原则：`SKILL.md` 只做入口和路由，不重复展开详细规则。需要具体规则时，读取对应 `references/` 文件。

## 启动方式

新项目推荐这样开始：

```text
使用 $project-create-rocky-0-1-0 帮我创建一个新项目。
先进入 PM 阶段，和我讨论需求，不要写代码。
等 PRD 确认后，再生成项目文档和后续流程。
```

用户须知：

- PM 阶段通常需要 2-5 轮对话，复杂项目会更多。
- 你不需要提前准备文档，只需要先说清“想做什么”。
- 完成后会得到一套可开工的项目文档、目录结构、角色入口和交接规则。

## 核心流程

```text
启用 skill
-> PM 需求探讨
-> 项目规模判断
-> PRD 确认
-> 生成 README / PRD / TASKS / HANDOFF / docs/agent-prompts
-> 手动进入 Architect / Builder / QA 等角色
-> PRD 后 GitHub 自动建库，只确认 public/private
```

角色交接是手动跨窗口交接，不在单窗口连续执行多个角色。除 GitHub 自动建库外，其他角色流程默认手动。

## 触发式路由表

按触发条件读取，不要一次性读完所有 references。

| 触发条件 | 读取文件 |
|---|---|
| 用户说“创建新项目” | `references/pm-discovery-flow.md` -> `references/project-scale-rules.md` -> `references/output-file-templates.md` |
| PM 前 1-2 轮探讨 | `references/project-scale-rules.md` |
| PM 确认 PRD 后 | `references/output-file-templates.md` -> `references/readme-role-entry.md` -> `references/github-automation-rules.md` |
| 用户说“进入 PM” | `references/role-delivery-rules.md` -> `references/roles/pm.md` |
| 用户说“进入 Architect” | `references/role-delivery-rules.md` -> `references/roles/architect.md` -> `references/validation-rules.md` |
| 用户说“进入 Builder” | `references/role-delivery-rules.md` -> `references/roles/builder.md` |
| 用户说“进入 QA” | `references/role-delivery-rules.md` -> `references/roles/qa.md` -> `references/validation-rules.md` |
| 用户说“进入 Reviewer” | `references/role-delivery-rules.md` -> `references/roles/reviewer.md` |
| 用户说“进入 Designer” | `references/role-delivery-rules.md` -> `references/roles/designer.md` -> `references/asset-and-data-rules.md` |
| 用户说“进入 DevOps/GitHub” | `references/role-delivery-rules.md` -> `references/roles/devops-github.md` -> `references/github-automation-rules.md` |
| 新窗口需要角色导航 | `references/readme-role-entry.md` -> `references/role-prompts.md` |
| 修改文件或运行命令前 | `references/safety-rules.md` |
| Builder 大改前或 QA 严重失败 | `references/rollback-rules.md` |
| GitHub、写文件、验证、部署失败 | `references/failure-recovery-rules.md` |
| 需要版本升级或兼容旧项目 | `references/versioning-strategy.md` |
| 需要解释 `agents/openai.yaml` 或多平台 | `references/platform-adapter-rules.md` |
| 需要来源、范围或迁移说明 | `references/source-map.md` |

## 新项目最低输出

具体结构以 `references/output-file-templates.md` 为准。

```text
README.md
AI_RULES.md
PRD.md
PRD_CURRENT.md
TASKS.md
HANDOFF.md
PROJECT_STRUCTURE.md
ARCHITECTURE.md
CHANGELOG.md
docs/prd/
docs/agent-prompts/
docs/reports/
```

## 新手说明要求

执行修改文件、运行命令、访问外部账号、处理 GitHub 或凭据前，必须说明：

```text
我要做什么
为什么要这样做
会改哪些文件或运行哪些命令
有什么风险
成功标志是什么
```

教程类内容必须写成开发新手可以照着做的步骤，并标注成功标志。
