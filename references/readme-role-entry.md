# README Role Entry

本文件定义新项目 `README.md` 里必须包含的角色入口导航。

目的：让用户新开窗口时，只要让 AI 读取 `README.md`，AI 就能知道下一步应该读取哪个职位 prompt，而不需要用户复制粘贴完整提示词。

## 项目内职位提示词目录

新项目创建时，必须生成：

```text
docs/agent-prompts/
  pm.md
  architect.md
  builder.md
  reviewer.md
  qa.md
  designer.md
  devops-github.md
```

这些文件来自 skill 内部模板：

```text
references/roles/pm.md
references/roles/architect.md
references/roles/builder.md
references/roles/reviewer.md
references/roles/qa.md
references/roles/designer.md
references/roles/devops-github.md
```

## README 必备小节模板

把下面内容写入项目 `README.md`：

~~~md
## Agent Role Entry

本项目使用 `$project-create-rocky-0-1-0` 规则。

新窗口开始前，先读取：

1. `HANDOFF.md`
2. `TASKS.md`
3. `PRD_CURRENT.md`
4. `PROJECT_STRUCTURE.md`
5. 当前职位提示词：`docs/agent-prompts/<role>.md`

职位提示词：

- PM：`docs/agent-prompts/pm.md`
- Architect：`docs/agent-prompts/architect.md`
- Builder：`docs/agent-prompts/builder.md`
- Reviewer：`docs/agent-prompts/reviewer.md`
- QA：`docs/agent-prompts/qa.md`
- Designer：`docs/agent-prompts/designer.md`
- DevOps/GitHub：`docs/agent-prompts/devops-github.md`

角色交接是手动跨窗口交接。每个角色完成后，只写清交接信息，不自动切换到下一角色。

### 一键启动命令

Builder：

```text
使用 $project-create-rocky-0-1-0，进入 Builder 模式。
请读取 README.md，并按 Agent Role Entry 导航读取 Builder 所需文件。
只执行 Builder 职责，完成后写清交接，不要切换到 QA。
```

QA：

```text
使用 $project-create-rocky-0-1-0，进入 QA 模式。
请读取 README.md，并按 Agent Role Entry 导航读取 QA 所需文件。
只执行 QA 职责，完成后写清交接，不要切换到 Builder。
```

Architect：

```text
使用 $project-create-rocky-0-1-0，进入 Architect 模式。
请读取 README.md，并按 Agent Role Entry 导航读取 Architect 所需文件。
只执行 Architect 职责，完成后写清交接，不要切换到 Builder。
```
~~~

## 新窗口示例

Builder 窗口：

```text
使用 $project-create-rocky-0-1-0，进入 Builder 模式。
请读取 README.md，并按 Agent Role Entry 导航读取 Builder 所需文件。
只执行 Builder 职责，完成后写清交接，不要切换到 QA。
```

QA 窗口：

```text
使用 $project-create-rocky-0-1-0，进入 QA 模式。
请读取 README.md，并按 Agent Role Entry 导航读取 QA 所需文件。
只执行 QA 职责，完成后写清交接，不要切换到 Builder。
```

## 成功标志

```text
README.md 包含 Agent Role Entry 小节
docs/agent-prompts/ 存在
每个职位都有单独 prompt 文件
新窗口能从 README 导航到当前职位 prompt
```
