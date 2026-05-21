# Role Prompts Index

本文件只做职位提示词索引，不放完整提示词。

这样做的目的：

- 新窗口只读取当前职位文件，节省 token。
- 避免 Builder 读到 QA、PM、DevOps/GitHub 的完整规则后串角色。
- README 可以用本索引把用户导航到正确职位文件。

## 使用规则

- 进入某个职位前，先读取 `references/role-delivery-rules.md`。
- 再只读取当前职位的独立 prompt 文件。
- 角色只能在自己的默认可写范围内工作。
- 如果需要越界，先说明原因和风险，再请求用户确认。
- 每个角色完成后都要更新或建议更新 `HANDOFF.md`。
- 角色交接是手动跨窗口交接，不在单窗口连续执行多个角色。

## 职位文件

| 职位 | 读取文件 |
|---|---|
| PM | `references/roles/pm.md` |
| Architect | `references/roles/architect.md` |
| Builder | `references/roles/builder.md` |
| Reviewer | `references/roles/reviewer.md` |
| QA | `references/roles/qa.md` |
| Designer | `references/roles/designer.md` |
| DevOps/GitHub | `references/roles/devops-github.md` |

## 新窗口推荐说法

Builder 示例：

```text
使用 $project-create-rocky-0-1-0，进入 Builder 模式。
请读取 README.md、HANDOFF.md、TASKS.md、PRD_CURRENT.md、ARCHITECTURE.md、PROJECT_STRUCTURE.md。
再读取 docs/agent-prompts/builder.md。
只执行 Builder 职责，完成后写清交接，不要切换到 QA。
```

QA 示例：

```text
使用 $project-create-rocky-0-1-0，进入 QA 模式。
请读取 README.md、HANDOFF.md、TASKS.md、PRD_CURRENT.md、docs/reports/implementation/。
再读取 docs/agent-prompts/qa.md。
只执行 QA 职责，完成后写清交接，不要切换到 Builder。
```

## QA -> Builder -> QA 手动交接

```text
QA 测试失败
-> QA 写清复现步骤和失败原因
-> 用户新开 Builder 窗口或指定 Builder 继续
-> Builder 根据 QA 报告修复
-> Builder 写清修复结果和验证建议
-> 用户新开 QA 窗口或指定 QA 再测
```

停止条件：

```text
QA 通过
或用户决定暂停
或发现需求不清，需要回到 PM
或发现架构问题，需要回到 Architect
```
