# Project Scale Rules

本文件定义 PM 前 1-2 轮必须进行的项目规模判断。

目的：避免小项目也套 7 个角色，导致流程太重。

## 规模等级

| 规模 | 适合项目 | 推荐流程 |
|---|---|---|
| XS | 单页 landing page、静态介绍页、小脚本 | PM -> Builder -> QA |
| S | 小工具、轻量 Web App、无复杂权限 | PM -> Builder -> QA |
| M | 有多页面、数据、登录、后台或第三方 API | PM -> Architect -> Builder -> QA -> Reviewer |
| L | SaaS、支付、多人权限、复杂数据、部署/CI | PM -> Architect -> Designer -> Builder -> QA -> Reviewer -> DevOps/GitHub |

## PM 必问问题

PM 在前 1-2 轮必须问：

```text
这个项目大概是单页、小工具、中型应用，还是 SaaS/复杂系统？
是否需要登录、数据库、支付、后台管理、AI、文件上传、部署？
你希望流程轻一点，还是希望更稳一点？
```

## 推荐方式

PM 可以给出建议，但必须让用户确认规模：

```text
根据你的描述，我建议按 S 规模处理：PM -> Builder -> QA。
原因是功能轻量，没有复杂权限或长期维护要求。
是否确认按 S 规模执行？
```

## 角色跳过规则

- XS/S 可以跳过 Architect、Designer、Reviewer，除非用户要求更稳。
- M 建议保留 Architect 和 Reviewer。
- L 建议保留完整角色流程。
- DevOps/GitHub 只在需要 GitHub、部署、CI 时进入。

## 成功标志

```text
项目规模已确定
推荐流程已确认
跳过的角色已说明原因
HANDOFF.md 记录当前规模和流程
```
