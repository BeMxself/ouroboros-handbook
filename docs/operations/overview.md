---
title: 运维总览
sidebar_position: 2
---

# 运维总览

潮汐栈的运维工作不只是“把平台跑起来”，还包括应用发布、环境维护、升级回滚和故障排查。

## 运维主线

1. 确认部署架构
2. 准备环境与依赖
3. 完成平台安装与初始化
4. 发布应用并维护运行环境
5. 做好升级、回滚、备份和排障

## 先看哪里

- [部署架构](./deployment-architecture)
- [环境要求](./environment-requirements)
- [安装与初始化](./installation-and-initialization)

## 运维侧需要额外关注的内建能力

- 调度任务：涉及任务执行节点、触发策略和运行状态维护
- 消息队列：涉及中间件准备、连接治理和消费运行状态
- 文件上传与文档管理：涉及存储路径、访问地址、容量和清理策略
- 业务日志：适合用于操作审计、问题回溯和变更追踪

如果你在做实施方案或部署边界梳理，建议先结合 [平台能力地图](../reference/platform-capability-map) 一起看。

如果你准备把这些能力纳入正式环境维护，继续看 [运行能力维护要点](./runtime-capability-maintenance)。

如果你想把调度任务、RabbitMQ 和 WebSocket 当成独立运行链路治理，继续看 [任务、消息与实时链路维护](./task-message-and-realtime-link-maintenance)。

如果你要把“谁做了什么、结果如何”纳入正式回溯链路，继续看 [业务日志与审计回溯](./business-logs-and-audit-traceability)。

如果你要把环境、容器和版本治理一起纳入交付流程，也可以补看 [开发平台辅助能力](../fusion-development/development-platform-support-capabilities)。

## 补充入口

新的运维主线已经覆盖环境准备、安装与初始化等核心入口。若你当前需要继续下钻，建议优先顺着下面两页继续：

- [环境要求](./environment-requirements)
- [安装与初始化](./installation-and-initialization)
