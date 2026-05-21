# Project Structure 项目结构规则

用于普通网站、应用、工具、内容项目或小型产品原型。

## 根目录

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
package.json
```

根据技术栈可能出现：

```text
src/
app/
pages/
public/
tests/
tools/
scripts/
.github/
```

## 文档目录

```text
docs/
  prd/
  agent-prompts/
  design/
  reports/
  assets/
```

规则：

- `docs/prd/` 放版本化需求文档。
- `docs/agent-prompts/` 放项目内职位提示词，新窗口按角色只读取对应文件。
- `docs/design/` 放设计说明、交互说明、参考资料。
- `docs/reports/` 放 Agent 或人工工作报告。
- `docs/assets/` 放资源说明，不默认放正式运行资源。

角色报告推荐拆成：

```text
docs/reports/architecture/
docs/reports/implementation/
docs/reports/qa/
docs/reports/review/
docs/reports/design/
docs/reports/devops/
```

对应关系：

- Architect 写 `docs/reports/architecture/`。
- Builder 写 `docs/reports/implementation/`。
- QA 写 `docs/reports/qa/`。
- Reviewer 写 `docs/reports/review/`。
- Designer 写 `docs/reports/design/`。
- DevOps/GitHub 写 `docs/reports/devops/`。

## 源代码目录

```text
src/
app/
pages/
components/
lib/
utils/
```

规则：

- 源代码负责“项目如何运行”。
- 不要把大量正文内容、故事内容、运营文案硬编码进运行逻辑。
- 共享逻辑放到 `lib/` 或 `utils/`，避免复制粘贴到多个页面。
- `.github/` 只放 GitHub Actions、Issue 模板、PR 模板等仓库配置文件，由 DevOps/GitHub 角色维护。

## 草稿与输出

```text
drafts/
output/
tmp/
```

规则：

- `drafts/` 放未确认草稿。
- `output/` 放 AI 生成候选文件。
- `tmp/` 放临时文件。
- 这些目录里的内容默认不是正式交付物。

## 正式资源

```text
public/assets/
```

规则：

- 只有确认过的图片、音频、视频、图标等资源才放这里。
- 正式页面不要引用 `output/` 里的临时资源。
- 私密数据不要放到 `public/`。

## 私密或运行数据

```text
storage/
.env
.env.local
```

规则：

- 不提交真实 API Key、密码、session、用户数据。
- `.env` 类文件通常要加入 `.gitignore`。
- 如果不确定某个文件是否敏感，先问用户或默认不提交。
