# Rollback Rules

本文件定义 Builder 修改失败或 QA 发现严重问题时的回滚策略。

## 基本原则

- 不随意执行破坏性 Git 命令。
- 回滚前先说明风险。
- 优先用 commit、diff、patch 记录可回退点。
- 如果工作区有用户未提交改动，不能直接覆盖。

## Builder 大改前

Builder 在大改前应建议建立 checkpoint：

```text
当前要进行较大改动，建议先创建 checkpoint commit，方便 QA 失败时对比或回退。
风险：commit 会写入 Git 历史，但不会上传远程，除非后续 push。
成功标志：git status 干净，产生一个 checkpoint commit。
```

如果用户不想 commit，可以至少记录：

```text
git status
git diff --stat
当前修改范围
```

## QA 失败后

QA 失败时，不直接回滚。先输出：

```text
失败功能
复现步骤
预期结果
实际结果
疑似相关文件
建议 Builder 修复还是回滚
```

## 回滚方式

允许的低风险方式：

- 用新 commit 修复问题。
- 用补丁反向修改本次变更。
- 对比 checkpoint commit 找出差异。

高风险方式：

```powershell
git reset --hard
git clean -fd
```

高风险方式只有用户明确要求，并确认会丢失哪些改动后才能执行。

## 成功标志

```text
问题已修复或已回到可用状态
用户改动没有被覆盖
HANDOFF.md 记录失败原因和处理结果
QA 可以重新验证
```
