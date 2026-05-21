# GitHub Automation Rules

本规则用于让 AI 在 PM 确定 PRD 后，自动化创建 GitHub 仓库、登记远程地址并推送项目。

目标是减少新手需要手动判断的步骤。仓库名、remote、初始化 commit、push 等由 AI 根据项目上下文自动处理；用户只需要确认仓库公开状态。

## 执行时机

GitHub 自动化发生在：

```text
PM 与用户完成需求讨论
-> PM 写好 PRD / PRD_CURRENT / TASKS / HANDOFF
-> PM 确认 PRD 已定稿或进入当前版本基线
-> AI 询问仓库 public 还是 private
-> AI 自动创建 GitHub 仓库并登记
```

## 唯一需要确认的问题

创建仓库前只问用户：

```text
这个 GitHub 仓库要公开 public，还是私密 private？
```

不再询问：

- 仓库名称。
- 仓库描述。
- 是否创建 README。
- 是否创建 `.gitignore`。
- 是否创建 license。
- 是否设置 remote。
- 是否首次 commit。
- 是否首次 push。

这些由 AI 按 PRD、项目目录和当前工程状态自动决定。

## 自动命名规则

仓库名按顺序取值：

1. `PRD.md` 或 `PRD_CURRENT.md` 里的项目名。
2. `README.md` 里的项目名。
3. 当前本地项目文件夹名。

命名转换规则：

- 使用 GitHub 友好的英文小写短横线格式。
- 空格转成 `-`。
- 删除不适合仓库名的符号。
- 中文项目名自动转成简短英文或拼音 slug。
- 如果仓库名已存在，自动追加短后缀，例如 `-2` 或日期后缀。

## 默认账号规则

- 默认使用当前已登录的 GitHub 账号或当前可用的 GitHub 工具连接。
- 不把“账号或组织”作为常规提问项。
- 如果当前环境没有 GitHub 登录状态，或工具无法判断可用账号，提示用户先完成 GitHub 登录或连接。
- 如果同一个账号下仓库名冲突，自动换名并记录实际仓库名。

## 风险解释

必须用新手能懂的话解释：

- public 仓库：别人可能看到你的代码和文件。
- private 仓库：外部默认看不到，但你仍然不能提交密钥、密码、token、session。
- git remote：相当于给本地项目登记一个 GitHub 上传地址，之后 push 会默认发到这里。
- commit：把当前改动打包成一个版本。
- push：把这个版本上传到 GitHub。

## 推荐流程

```text
PM 确认 PRD
-> 询问 public/private
-> 检查敏感文件
-> 自动生成仓库名
-> 创建 GitHub 仓库
-> 本地 git init 或检查已有 Git
-> 设置 git remote
-> commit
-> push
-> 在 HANDOFF.md 记录仓库地址和当前状态
```

## 禁止事项

- 未确认 public/private，不创建仓库。
- 未检查敏感文件，不 push。
- 不把 API Key、密码、token、session、用户数据提交到 GitHub。
- 不在用户不知情时切换远程仓库地址。
- 不因为仓库名冲突就停下来问新手命名细节；应自动追加后缀并记录。

## 成功标志

执行完成后说明：

```text
GitHub 仓库地址
仓库公开状态 public/private
本地 remote 名称
最新 commit hash
push 是否成功
HANDOFF.md 是否已记录
```
