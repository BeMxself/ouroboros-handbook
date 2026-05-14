---
title: 运维管理
sidebar_position: 1
---

# 运维管理

适用对象：负责部署、升级、维护和排障的实施与运维人员。

这部分围绕部署、升级、恢复和排障组织，目标是帮助团队把潮汐栈从“能跑起来”推进到“可持续维护”。

## 建议阅读顺序

1. [运维总览](./overview)
2. [部署架构](./deployment-architecture)
3. [环境要求](./environment-requirements)
4. [安装与初始化](./installation-and-initialization)
5. [升级、回滚与维护](./release-upgrade-and-rollback)
6. [备份、监控与排障](./backup-monitoring-and-troubleshooting)

## 你会在这里看到什么

- 环境要求和部署架构
- 初始化和应用发布
- 升级、回滚与维护
- 日志、监控和故障排查
- 与任务调度、消息、文件和业务日志相关的运行维护关注点

如果你需要先盘点平台有哪些“会影响部署和维护方案”的能力，可以先看 [平台能力地图](../reference/platform-capability-map)。

如果你已经明确会用到文件、文档、调度、消息或 WebSocket，建议继续看 [运行能力维护要点](./runtime-capability-maintenance)。

如果你现在更关心的是调度任务、RabbitMQ 和 WebSocket 这些链路如何日常维护，建议继续看 [任务、消息与实时链路维护](./task-message-and-realtime-link-maintenance)。

如果你已经开始关注操作审计、责任追踪和问题回放，建议继续看 [业务日志与审计回溯](./business-logs-and-audit-traceability)。

如果你在准备应用的环境划分、容器运行和版本发布协同，也可以先补看 [开发平台辅助能力](../fusion-development/development-platform-support-capabilities)。

如果你当前只是要在本地或体验环境先把平台运行起来，可以先走 [快速上手](../getting-started/)；当你开始准备团队环境、持续维护或版本升级时，再回到这里。

## 补充阅读

- 如果你是第一次接触平台，建议先完成 [快速上手](../getting-started/)
- 如果你需要继续细化安装细节，建议结合 [环境要求](./environment-requirements) 和 [安装与初始化](./installation-and-initialization) 一起阅读
