# Project Create Rocky 0.1.0

`project-create-rocky-0-1-0` 是一个面向 AI Coding 新手的 Codex skill。

它的目标是帮助用户从“我有一个想法”更快进入合规、清晰、可交接的开发流程：先由 PM 阶段梳理需求和项目规模，再生成 PRD、任务、交接、文件地图和角色提示词，最后让 Builder、QA、Reviewer 等角色可以按规则手动接力。

## 适合谁

- 第一次使用 AI 辅助写代码的开发新手。
- 想把项目从想法整理成 PRD、TASKS、HANDOFF 的用户。
- 想让不同 AI 窗口按 PM、Builder、QA 等职位手动协作的人。
- 想减少“直接开写代码但没有流程和验收标准”风险的项目。

## 核心能力

- PM 需求探讨：通过 1 到 N 轮对话，把模糊想法整理成 PRD。
- 项目规模判断：按 XS/S/M/L 判断流程轻重，小项目不强制套完整 7 角色。
- 文件模板：统一 `PRD.md`、`PRD_CURRENT.md`、`TASKS.md`、`HANDOFF.md`、`CHANGELOG.md` 等结构。
- 文件地图：定义项目目录、文档、报告、资源、私密数据放置规则。
- 职位提示词：为 PM、Architect、Builder、Reviewer、QA、Designer、DevOps/GitHub 提供独立 prompt。
- README 角色入口：新窗口只需读取 README，就能导航到当前职位 prompt。
- 手动跨窗口交接：角色之间不自动连续执行，由用户决定何时进入下一角色。
- GitHub 自动建库：PRD 确认后，可自动创建公开或私密仓库，只需要用户确认 public/private。
- 安全和回滚：修改文件、运行命令、Git、GitHub、部署前先说明风险；Builder 大改前建议 checkpoint。

## 推荐启动方式

```text
使用 $project-create-rocky-0-1-0 帮我创建一个新项目。
先进入 PM 阶段，和我讨论需求，不要写代码。
等 PRD 确认后，再生成项目文档和后续流程。
```

## 流程概览

```text
启用 skill
-> PM 需求探讨
-> 项目规模判断
-> PRD 确认
-> 生成 README / PRD / TASKS / HANDOFF / docs/agent-prompts
-> 手动进入 Architect / Builder / QA 等角色
-> PRD 后 GitHub 自动建库
```

## 文件地图

```text
SKILL.md                         skill 入口和触发式路由表
CHANGELOG.md                     skill 版本变化记录
agents/openai.yaml               OpenAI Codex UI 元信息
references/                      详细规则文档
references/roles/                各职位独立 prompt 模板
```

关键规则：

- `references/pm-discovery-flow.md`: PM 如何探讨需求并确认 PRD。
- `references/project-scale-rules.md`: 项目规模判断。
- `references/output-file-templates.md`: 输出文件结构模板。
- `references/readme-role-entry.md`: README 角色入口模板。
- `references/role-delivery-rules.md`: 每个职位的交付边界。
- `references/validation-rules.md`: 多技术栈验证命令。
- `references/rollback-rules.md`: Builder 大改和 QA 失败后的回滚策略。
- `references/github-automation-rules.md`: GitHub 建库规则。
- `references/failure-recovery-rules.md`: 常见失败处理。

## 角色交接说明

本 skill 不会让 PM、Builder、QA 在同一个窗口里自动连续执行。

推荐方式是用户按需要新开窗口，并说：

```text
使用 $project-create-rocky-0-1-0，进入 Builder 模式。
请读取 README.md，并按 Agent Role Entry 导航读取 Builder 所需文件。
只执行 Builder 职责，完成后写清交接，不要切换到 QA。
```

## 项目状态

当前版本是 `0.1.0`，主要用于建立稳定的项目创建流程、角色边界和文档规范。

计划中的 `0.2.0` 会考虑加入脚本化初始化、更多技术栈模板和更多平台适配。

## 注意事项

- 公开仓库不要提交真实 API Key、token、密码、session 或用户数据。
- 高风险 Git 命令，例如 `git reset --hard` 和 `git clean -fd`，必须由用户明确要求后才能执行。
- GitHub 建库只自动化仓库创建、remote、commit、push；其它角色流程默认手动。
