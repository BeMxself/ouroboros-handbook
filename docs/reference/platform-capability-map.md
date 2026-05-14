---
title: 平台能力地图
sidebar_position: 2
---

# 平台能力地图

适用对象：已经理解平台主路径，但想快速盘点“潮汐栈当前已经内建了哪些能力”的读者。

这页不是详细教程，更像一张能力盘点表。你可以先在这里判断平台是否已经覆盖了你的需求，再决定继续走低代码、进入融合开发，还是补充运维方案。

## 怎么使用这页

- 当你要判断一个需求能不能先用平台现成能力解决时，先看这里
- 当你在“继续配置”还是“开始写代码”之间犹豫时，先看这里
- 当你要做实施、部署或集成方案梳理时，也建议先看这里

## 能力总览

| 能力领域       | 当前平台能力                                                                      | 主要面向谁           | 推荐入口                                                     |
| -------------- | --------------------------------------------------------------------------------- | -------------------- | ------------------------------------------------------------ |
| 业务交付主线   | 应用管理、业务模型、页面/菜单、逻辑流、审批流、组织架构、身份与访问控制、字典、配置项、通知 | 业务开发、实施人员   | [低代码开发](../low-code/)、[核心概念](../concepts/)         |
| 文件与内容     | 文件上传、字段附件接入、文档库、目录、文档预览/下载、细粒度文档权限               | 业务开发、平台实施   | 本页、[低代码开发](../low-code/)                             |
| 集成与自动化   | Web API、RPC、逻辑流、调度任务、消息队列、WebSocket、通知                         | 专业开发、集成开发   | [融合开发](../fusion-development/)、[核心概念](../concepts/) |
| 门户与前端体验 | Widget、小组件、用户仪表板、快捷入口、用户信息、平台组件库、微前端扩展            | 前端开发、融合开发   | [融合开发](../fusion-development/)                           |
| 开发平台辅助   | 版本治理、数据源管理、环境管理、容器支撑、应用版本与调试辅助                      | 专业开发、平台管理员 | 本页、[运维管理](../operations/)                             |
| 运行与运维辅助 | 应用运行时、配置管理、业务日志、升级回滚、备份排障                                | 运维、实施人员       | [运维管理](../operations/)                                   |

## 业务交付与内容能力

- 低代码主线已经覆盖应用创建、业务模型、页面表单、菜单、逻辑流、审批流、组织架构、身份/访问边界、字典、配置项和通知等核心能力，适合完成大部分标准业务交付。
- `dynamic-form` 支持定义动态表单、部署表单，并生成表单页和表格页，适合做轻量采集、登记、台账类场景。
- `ui-schema-management` 支持把自定义 UI Schema 作为可管理资源维护，适合做页面模板、特定页面覆写或运行时界面定制。
- `ouroboros-file-upload` 提供统一上传入口、文件访问地址生成、存储后端适配、临时文件清理和字段接入能力。
- `document-management` 提供文档库、目录树、上传/下载/预览和细粒度权限控制，适合承接共享资料、制度文档、业务附件沉淀等场景。

## 集成、自动化与实时能力

- 调度能力由 `ouroboros-scheduler` 提供，支持 Cron 和一次性任务调度，并能把调度结果接到 LogicFlow 执行链路上。
- 消息队列能力由 `ouroboros-message-queue` 提供，当前默认适配 RabbitMQ，并支持绑定管理、发送/消费和低代码运行时接入。
- 实时双向通信能力由 `ouroboros-websocket` 提供，基于 STOMP 处理消息发送、订阅、连接鉴权和会话级路由。
- 这些能力意味着平台不只适合“表单加流程”，也适合承接定时任务、异步解耦、状态推送和外部系统协同。
- 如果你的目标是复用这些现成底座，而不是从零自建集成框架，建议先看 [融合开发总览](../fusion-development/overview) 和 [平台扩展点总表](../fusion-development/extension-points)。

## 门户、组件与用户体验能力

- `ouroboros-widget` 提供 Widget 定义、Widget Schema、运行时加载和管理入口，内建表格、列表、图表等常用小组件。
- Widget 体系还包含用户仪表板模板、快捷入口和用户信息等模块，说明平台已经具备搭建工作台式首页的基础能力。
- `ouroboros-dev-platform-component-lib` 支持上传、安装、分发和版本管理平台组件库，并允许应用按需导入组件库。
- 这意味着很多前端个性化需求并不一定要直接改主应用代码，也可以先评估“组件库 + Widget + 微前端”这条路线。

## 开发平台辅助能力

- `ouroboros-dev-version-control-system` 把 Git 封装成平台可用的版本治理能力，覆盖文件操作、提交、锁定、差异和版本记录等场景。
- `ouroboros-dev-datasource` 支持平台级数据源、应用级数据源绑定，以及 JDBC 数据表元数据读取，适合做外部库接入和多数据源管理。
- `ouroboros-dev-environment` 提供开发、测试、验收、生产等环境定义聚合，方便把开发和发布行为落到明确环境语义下。
- `ouroboros-dev-container` 提供容器生命周期管理、镜像拉取和状态事件监听，为开发平台的容器化运行支撑能力打底。
- 开发平台本身还包含应用版本、容器控制、扩展 Jar、调试辅助等应用管理能力，适合支撑从开发到交付的持续演进。

## 运行与运维辅助能力

- `ouroboros-business-log` 会把 HTTP 侧业务动作沉淀为统一业务日志，适合做操作审计、行为追踪和问题回溯。
- 文件上传、文档管理、调度任务、消息队列、WebSocket 这些能力都意味着运维侧需要同步考虑存储、任务、消息中间件和连接治理。
- 如果你当前关注的是部署、初始化、升级、回滚、备份和排障，主入口仍然是 [运维管理](../operations/)。

## 哪些内容已经有详细章节

- 低代码主线：见 [低代码开发](../low-code/)
- 低代码基础能力：见 [组织、权限、配置与通知](../low-code/organization-permissions-configuration-and-notification)
- 低代码流程与自动化：见 [流程、规则与自动化](../low-code/workflow-rules-and-automation)
- 低代码页面交付：见 [页面交付：标准页面、动态表单与 UI Schema](../low-code/page-delivery-with-dynamic-forms-and-ui-schema)
- 表单、附件与文档：见 [表单、附件与文档能力](../low-code/forms-attachments-and-documents)
- 扩展机制：见 [融合开发](../fusion-development/)
- 集成、自动化与实时能力：见 [集成、自动化与实时能力](../fusion-development/integration-automation-and-realtime)
- 工作台与前端复用：见 [工作台、Widget 与平台组件库](../fusion-development/workbench-widgets-and-component-libraries)
- 开发平台辅助能力：见 [开发平台辅助能力](../fusion-development/development-platform-support-capabilities)
- 部署与维护：见 [运维管理](../operations/)
- 运行能力维护：见 [运行能力维护要点](../operations/runtime-capability-maintenance)
- 任务、消息与实时链路维护：见 [任务、消息与实时链路维护](../operations/task-message-and-realtime-link-maintenance)
- 审计回溯：见 [业务日志与审计回溯](../operations/business-logs-and-audit-traceability)
- 模型与术语：见 [核心概念](../concepts/)
- 接口、SDK、DSL：见 [API 参考总览](../api/)

## 哪些内容目前仍以能力说明为主

下面这些方向在当前手册里已经补充到能力地图，但更细的专题或操作文档仍然相对不足，后续会继续补齐：

- 动态表单、UI Schema 管理、文档管理
- 文件上传与文件存储策略
- Widget 的场景化落地方法
- 数据源、环境、容器、版本治理、平台组件库
