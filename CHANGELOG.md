# Changelog

## 0.1.0

初始 Rocky 版。

- 建立 PM -> Architect -> Builder -> QA -> Reviewer -> DevOps/GitHub 的手动跨窗口交接规则。
- 建立 PM 需求探讨到 PRD 确认的流程。
- 建立 README Agent Role Entry 导航规则。
- 建立项目内 `docs/agent-prompts/<role>.md` 职位提示词规则。
- GitHub 建库只保留 public/private 一个用户决策点。

## 计划中的 0.2.0

候选方向：

- 增加项目初始化脚本，把 reference 模板复制到新项目。
- 增加更多技术栈模板，例如 Python、Go、静态站、Next.js、CLI 工具。
- 增加更细的部署平台规则，例如 Vercel、GitHub Pages、Docker。
- 增加多平台 AI 接口元数据，例如 OpenAI、通用 Markdown、其他 Agent 平台。

## 兼容策略

- 0.1.x 只做文档规则补强，不破坏已生成项目的文件名。
- 0.2.0 可以新增文件，但默认不重命名 `PRD.md`、`TASKS.md`、`HANDOFF.md`、`docs/agent-prompts/`。
- 已有项目升级时，优先追加新小节，不覆盖用户已经写过的正文。
