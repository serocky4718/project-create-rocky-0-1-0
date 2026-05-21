# Safety 安全规则

用于修改文件、运行命令、处理账号、部署和 Git 操作前的风险判断。

遇到失败时，先读 `references/failure-recovery-rules.md`，不要静默重试高风险操作。

## 修改文件前

先说明：

- 会修改哪些文件。
- 为什么需要修改。
- 是否可能影响现有功能。
- 是否会覆盖用户已有内容。

如果发现文件里有用户刚改过的内容，不要随意回滚。

## 运行命令前

先说明命令目的和风险。

低风险命令示例：

```powershell
Get-ChildItem
Get-Content
npm run build
```

高风险命令示例：

```powershell
Remove-Item -Recurse
git reset --hard
git clean -fd
```

高风险命令只有在用户明确要求时才执行。

## 外部账号和凭据

访问这些内容前要提醒用户：

- GitHub、Vercel、云服务、数据库后台。
- 可能产生费用的 API。
- 真实 API Key、密码、token、session。

默认不把凭据写进代码，不把凭据提交到 Git。

## Git 规则

- 不随意 `git reset --hard`。
- 不随意删除未跟踪文件。
- 不回滚用户未要求回滚的改动。
- 提交前说明提交范围。
- 大改前建议创建 checkpoint commit，详见 `references/rollback-rules.md`。
- 如果工作区有用户未提交改动，先说明，不覆盖。
- push 前必须检查 `.env`、密钥、token、session、用户数据。
- 回滚前必须说明会丢失哪些改动，并获得用户明确确认。
- 如果 `git status` 显示有不明来源改动，先询问或记录，不假设可以丢弃。
- 不使用 `git clean -fd` 清理文件，除非用户明确知道会删除未跟踪文件。
- 不为了让测试通过而隐藏、删除、跳过失败信息。

## GitHub 规则

- PRD 确认前不创建 GitHub 仓库。
- 未确认 public/private 前不创建 GitHub 仓库。
- GitHub 建库规则详见 `references/github-automation-rules.md`。
- GitHub 建库失败时，按 `references/failure-recovery-rules.md` 处理，不重复创建多个仓库。

## 部署规则

- 未经用户允许不部署到公网。
- 部署前说明可能产生费用、公开访问、环境变量泄露等风险。
- 生产环境配置不随意修改。
- 部署失败时，先报告失败原因，不反复部署刷日志。

## 文件写入失败

- 目录不存在时，可以创建目录，但要先说明。
- 权限不足或文件占用时，不假装写入成功。
- 写入失败要报告失败文件、原因和建议下一步。
