# Source Map 来源说明



## 保留的通用能力

- 项目入口文件规则。
- PRD、TASKS、HANDOFF 交接流程。
- 多角色协作边界。
- PM 需求探讨到 PRD 确认的流程。
- PM、Architect、Builder、Reviewer、QA、Designer、DevOps/GitHub 职位提示词。
- README Agent Role Entry 角色入口导航。
- 项目内 `docs/agent-prompts/<role>.md` 职位提示词。
- QA -> Builder -> QA 的跨窗口交接路线，不做单窗口连续执行。
- 项目规模判断，按 XS/S/M/L 选择流程。
- 核心输出文件模板，统一 PRD、TASKS、HANDOFF 等结构。
- 多技术栈验证命令选择。
- Builder checkpoint 和回滚策略。
- skill 版本演进和兼容策略。
- 报告目录规范。
- 资源和数据安全规则。
- 修改文件、运行命令、访问凭据前说明风险。
- PRD 确认后 GitHub 自动建库，只确认 public/private。

## 弱化或移除的专用内容

- galgame 专用内容包结构。
- `games/<gameId>/versions/<versionId>/` 专用结构。
- 叙事游戏专用 CLI 命令。
- 角色、场景、背包、任务等游戏数据结构。

## 适用范围

适合：

- 网站项目。
- Web App。
- 小工具。
- 内容型项目。
- 原型产品。
- 多 Agent 协作项目。

## 新增 Rocky 版重点

- 新项目必须先启用 skill，再进入 PM 探讨。
- PM 可以维护 PRD、PRD_CURRENT、TASKS、HANDOFF、CHANGELOG，但不写业务代码。
- 不同职位都有独立提示词和交付边界。
- README 只做导航牵引，完整职位 prompt 放在项目内 `docs/agent-prompts/`。
- GitHub 仓库名从项目名生成，不反复询问新手命名细节。
- `SKILL.md` 只做路由表，详细规则放在 `references/`，减少重复和 token 消耗。
