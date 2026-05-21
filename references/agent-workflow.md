# Agent Workflow 角色协作规则

用于创建或维护多人/多 Agent 协作项目。

## 必备入口文件

- `README.md`: 项目入口、快速开始、阅读顺序。
- `AI_RULES.md`: Agent 行为规则、权限边界、安全要求。
- `PRD.md`: 产品目标和总体范围。
- `PRD_CURRENT.md`: 当前活跃版本和阶段状态。
- `TASKS.md`: 当前迭代任务列表。
- `HANDOFF.md`: 最新交接信息和下一步说明。
- `PROJECT_STRUCTURE.md`: 文件地图和归属规则。
- `ARCHITECTURE.md`: 当前架构和模块边界。

内容型项目可以额外添加：

- `STORY_RULES.md`: 故事、角色、世界观、文风规则。
- `docs/story/`: 故事设定和内容资料。
- `docs/content/`: 内容结构和内容规范。

## 推荐阅读顺序

新项目启动时，优先读：

1. `SKILL.md`
2. `references/pm-discovery-flow.md`
3. `references/project-scale-rules.md`
4. `references/output-file-templates.md`
5. `references/role-delivery-rules.md`
6. `references/role-prompts.md`
7. `references/readme-role-entry.md`

项目文件已生成后，Agent 开工前优先读：

1. `README.md`
2. `AI_RULES.md`
3. `PRD_CURRENT.md`
4. `TASKS.md`
5. `HANDOFF.md`
6. `PROJECT_STRUCTURE.md`
7. `docs/reports/` 下对应角色报告
8. `docs/agent-prompts/<role>.md`

## 角色权限

Rocky 版默认规则：PM 负责产品和项目管理文档，包括 PRD、当前版本状态、任务、交接和变更记录。代码、配置、依赖安装、构建、部署、Git 写入不属于 PM 默认职责。

| 文件或目录 | 推荐负责人 |
|---|---|
| `PRD.md` | PM / Product Owner |
| `PRD_CURRENT.md` | PM / Product Owner |
| `TASKS.md` | PM |
| `HANDOFF.md` | PM、Architect、Builder、QA 按阶段更新 |
| `CHANGELOG.md` | PM，必要时由 Builder 补充技术变更 |
| `docs/prd/<version>/` | PM / Product Owner |
| `AI_RULES.md` | Architect / PM |
| `ARCHITECTURE.md` | Architect |
| `PROJECT_STRUCTURE.md` | Architect |
| `docs/reports/architecture/` | Architect |
| `src/`、`app/`、`pages/`、`components/`、`lib/`、`utils/` | Builder |
| `tests/` | Builder / QA |
| `docs/reports/implementation/` | Builder |
| `docs/reports/qa/` | QA |
| `docs/reports/review/` | Reviewer |
| `docs/design/`、`docs/assets/` | Designer |
| `docs/reports/design/` | Designer |
| `.github/`、部署配置、git remote | DevOps / GitHub |
| `docs/reports/devops/` | DevOps / GitHub |

## PM 交付规则

PM 开始写入前，必须先和用户完成一轮探讨，确认：

```text
目标
范围
优先级
验收标准
风险
下一步
```

确认后，PM 把结论写入：

```text
PRD.md
PRD_CURRENT.md
TASKS.md
HANDOFF.md
CHANGELOG.md
docs/prd/<version>/
```

PM 禁止：

- 修改代码。
- 修改配置。
- 安装依赖。
- 启动开发服务器。
- 运行构建或部署。
- 运行 Git 写入类命令。

PM 确定 PRD 后，可以触发 GitHub 自动建库流程。AI 创建仓库前只需要询问用户 public 还是 private；仓库名从项目名生成。

## 角色提示词规则

切换角色时，读取：

```text
README.md
docs/agent-prompts/<role>.md
HANDOFF.md
TASKS.md
PRD_CURRENT.md
references/role-delivery-rules.md
```

每个角色必须遵守：

- 只能在自己的默认可写范围内工作。
- 需要越界时，先说明原因、风险和成功标志，再请求用户确认。
- 完成后更新或建议更新 `HANDOFF.md`。
- 新窗口优先从 `README.md` 的 Agent Role Entry 小节导航到当前职位 prompt。

推荐跨窗口手动交接顺序：

```text
PM -> Architect -> Builder -> QA -> Reviewer -> DevOps/GitHub
```

这只是角色交接路线，不代表当前窗口要连续执行。每个角色完成后，只更新或建议更新 `HANDOFF.md`，等待用户决定是否开启下一角色。

失败交接路线：

```text
QA 失败 -> Builder 修复 -> QA 再测
需求不清 -> PM
架构不清 -> Architect
```

## 报告规则

不要在项目根目录随意新增报告文件。报告统一放到：

```text
docs/reports/architecture/
docs/reports/implementation/
docs/reports/qa/
docs/reports/review/
docs/reports/design/
docs/reports/devops/
```

文件名推荐：

```text
YYYY-MM-DD_<scope>.md
```

`HANDOFF.md` 要短，只写：

```text
当前阶段
已完成工作
稳定基线
下一位 Agent 指令
当前禁止事项
下一优先级
```

## 面向新手的说明方式

每次准备执行修改或命令时，说明：

- 我要做什么。
- 为什么要这样做。
- 会影响哪些文件或功能。
- 风险是什么。
- 成功标志是什么。
