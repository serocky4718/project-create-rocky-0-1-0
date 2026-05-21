# Output File Templates

本文件定义新项目核心输出文件的推荐结构。

目标：每次生成的 `PRD.md`、`TASKS.md`、`HANDOFF.md` 等文件格式一致。

## README.md

```md
# <项目名>

一句话说明项目做什么。

## Quick Start

## Agent Role Entry

## Project Docs

## Current Status
```

`Agent Role Entry` 详见 `references/readme-role-entry.md`。

## PRD.md

```md
# PRD: <项目名>

## 1. 背景
## 2. 目标用户
## 3. 要解决的问题
## 4. 项目目标
## 5. MVP 范围
## 6. 本阶段不做
## 7. 用户流程
## 8. 页面 / 模块清单
## 9. 数据和权限需求
## 10. 验收标准
## 11. 风险和待确认问题
```

## PRD_CURRENT.md

用途：记录当前正在执行的 PRD 版本，不替代完整 PRD。

```md
# Current PRD Status

## Active Version

## Current Scope

## Confirmed Decisions

## Open Questions

## Current Acceptance Criteria

## Next Role
```

关系：

- `PRD.md` 是完整产品需求。
- `PRD_CURRENT.md` 是当前执行切片和状态。
- 需求大改时更新 `PRD.md`。
- 当前阶段、当前范围、下一角色变化时更新 `PRD_CURRENT.md`。

## TASKS.md

```md
# Tasks

## Legend

- Status: `todo` / `doing` / `blocked` / `done`
- Priority: `P0` 必须 / `P1` 重要 / `P2` 可后置
- Owner: `PM` / `Architect` / `Builder` / `QA` / `Reviewer` / `Designer` / `DevOps`

## Current Sprint

| ID | Status | Priority | Owner | Task | Acceptance | Depends On |
|---|---|---|---|---|---|---|
| T-001 | todo | P0 | Builder | <任务> | <验收标准> | - |

## Backlog

## Blocked

## Done
```

## HANDOFF.md

```md
# Handoff

## Current Stage

## Completed Work

## Current State

## Verification Result

## Next Role

## Next Steps

## Risks

## Do Not Do
```

## CHANGELOG.md

```md
# Changelog

## <YYYY-MM-DD>

- Added:
- Changed:
- Fixed:
- Risk:
```

## PROJECT_STRUCTURE.md

```md
# Project Structure

## Root Files

## Source Code

## Docs

## Reports

## Assets

## Private Data

## Ownership

## Validation Commands
```

`Validation Commands` 记录当前项目实际采用的检查命令，例如 lint、test、build、启动本地服务等。具体选择规则见 `references/validation-rules.md`。

## ARCHITECTURE.md

```md
# Architecture

## Goals

## Tech Stack

## Module Boundaries

## Data Flow

## Risks and Tradeoffs
```
