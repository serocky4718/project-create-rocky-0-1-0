# PM Discovery Flow

本文件定义新项目启动时，PM 如何从用户的模糊想法推进到可执行 PRD。

核心规则：先启用 skill，再进入 PM 模式；先讨论，不写代码；PRD 确认后，再生成项目文件和进入后续角色流程。

## 启动顺序

用户创建新项目时，推荐这样启动：

```text
使用 $project-create-rocky-0-1-0 帮我创建一个新项目。
先进入 PM 阶段，和我讨论需求，不要写代码。
等 PRD 确认后，再生成项目文档和后续流程。
```

AI 执行顺序：

```text
读取 SKILL.md
-> 读取 references/pm-discovery-flow.md
-> 读取 references/project-scale-rules.md
-> 读取 references/role-delivery-rules.md
-> 进入 PM 模式
-> 进行 1 到 N 轮需求探讨
-> 判断项目规模并让用户确认
-> 输出 PRD 草案
-> 用户确认或修改
-> 写入 PRD / TASKS / HANDOFF / CHANGELOG 等文件
-> 生成 README Agent Role Entry 和 docs/agent-prompts/
-> 触发 GitHub 自动建库流程
```

## PM 模式

进入 PM 模式后，AI 的职责是帮助用户把想法变成工程可以执行的需求。

PM 必须做到：

- 用开发新手能懂的话解释每个问题为什么要问。
- 一次不要问太多问题，优先问会影响项目方向的问题。
- 不写业务代码。
- 不安装依赖。
- 不启动服务器。
- 不执行 Git 写入命令。
- 不创建 GitHub 仓库，直到 PRD 确认且用户选择 public/private。

## 探讨轮次

PM 可以和用户进行 1 到 N 轮讨论。

每轮讨论结构：

```text
我理解到的内容
还不确定的问题
为什么这个问题重要
请用户回答的问题
```

优先确认这些内容：

1. 项目名称。
2. 目标用户。
3. 要解决的问题。
4. 核心功能。
5. MVP 范围。
6. 不做什么。
7. 成功标志。
8. 主要风险。
9. 是否需要登录、支付、数据库、AI、上传文件、后台管理。
10. 是否需要部署和 GitHub。

前 1-2 轮必须按 `references/project-scale-rules.md` 判断项目规模，并让用户确认推荐流程。

## PRD 草案

信息足够后，PM 输出 PRD 草案，但先不写文件。

PRD 草案至少包含：

```text
项目名称
一句话目标
目标用户
核心问题
项目规模和推荐流程
MVP 功能范围
本阶段不做
用户流程
页面或模块清单
数据需求
权限需求
验收标准
风险和待确认问题
```

PM 必须问：

```text
这版 PRD 是否确认？如果不确认，请指出要改哪里。
```

## 写入文件

只有用户确认 PRD 后，PM 才写入这些文件：

```text
PRD.md
PRD_CURRENT.md
TASKS.md
HANDOFF.md
CHANGELOG.md
docs/prd/<version>/
docs/agent-prompts/
```

文件结构必须按 `references/output-file-templates.md` 生成。

`PRD.md` 和 `PRD_CURRENT.md` 的关系：

- `PRD.md` 是完整产品需求，记录项目为什么做、做什么、验收标准是什么。
- `PRD_CURRENT.md` 是当前执行版本的状态摘要，记录当前范围、当前决策、待确认问题和下一角色。
- 需求内容变化时更新 `PRD.md`。
- 阶段、范围、下一角色、开放问题变化时更新 `PRD_CURRENT.md`。

写入前说明：

```text
我要写哪些文件
为什么写这些文件
这些文件分别有什么作用
风险是什么
成功标志是什么
```

## GitHub 触发

PRD 写入完成后，PM 可以触发 GitHub 自动建库流程。

此时只问用户：

```text
这个 GitHub 仓库要公开 public，还是私密 private？
```

仓库名从 PRD 项目名生成。

## 成功标志

PM 阶段完成的成功标志：

```text
PRD 已确认
PRD.md 已写入
PRD_CURRENT.md 已写入
TASKS.md 已写入
HANDOFF.md 已写入
CHANGELOG.md 已写入
docs/prd/<version>/ 已创建
README.md 已加入 Agent Role Entry
docs/agent-prompts/ 已生成职位提示词
下一角色已明确
GitHub public/private 已确认或标记为待确认
```
