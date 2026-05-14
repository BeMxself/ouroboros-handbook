---
title: 融合开发
sidebar_position: 1
---

# 融合开发

适用对象：需要通过自定义代码扩展平台能力的专业开发人员。

融合开发关注的是一件事：什么场景适合继续用低代码，什么场景应该接入前后端代码扩展，以及两者如何协同。

## 起步建议

如果你刚从低代码主线切过来，建议先把下面几篇顺着看完，再决定进入前端扩展还是后端扩展：

1. [融合开发总览](./overview)
2. [何时用低代码，何时写代码](./when-to-use-code)
3. [平台能力地图](../reference/platform-capability-map)
4. [平台扩展点总表](./extension-points)
5. [高低开协同模式](./high-low-code-collaboration)

## 读完后怎么分流

- 如果需求核心是复杂页面、登录体验或微前端接入，继续看“前端扩展专题”
- 如果需求核心是字段、表达式、脚本或逻辑流能力扩展，继续看“后端扩展专题”
- 如果平台现成能力已经覆盖了调度、消息、实时通信、文件或 Widget 需求，优先复用内建能力
- 如果你发现需求其实仍在平台标准能力内，回到 [低代码开发](../low-code/)

如果你当前卡在“调度、消息、实时推送该怎么组合”，建议直接看 [集成、自动化与实时能力](./integration-automation-and-realtime)。

如果你当前卡在“工作台、Widget、平台组件库和微前端怎么选”，建议直接看 [工作台、Widget 与平台组件库](./workbench-widgets-and-component-libraries)。

如果你当前卡在“页面、登录页、布局组件、组件库和平台组件库该怎么分工”，建议直接看 [前端融合开发方式](./frontend-extension-paths)。

如果你当前卡在“自定义登录页怎么接微前端和认证能力”，建议直接看 [自定义登录页与认证接入](./custom-login-page-and-auth-integration)。

如果你当前卡在“后端能力应该怎么做成扩展包”，建议直接看 [创建后端扩展包](./backend-extension-packages)。

如果你当前卡在“开发平台里的 `*-dev` 模块和 Maven 脚手架怎么起”，建议直接看 [开发模块与 Maven 脚手架](./development-module-scaffold-and-maven-skeleton)。

如果你当前卡在“数据源、环境、容器和版本治理应该怎么协同”，建议直接看 [开发平台辅助能力](./development-platform-support-capabilities)。

如果你当前卡在“标准 RBAC 不够，主体、Claims 和细粒度访问控制应该怎么设计”，建议直接看 [权限、主体与访问控制设计](./authority-subject-and-access-control-design)。

## 前端扩展专题

- [前端融合开发方式](./frontend-extension-paths)
- [自定义登录页与认证接入](./custom-login-page-and-auth-integration)
- [微前端应用](../guide/advance/extend-frontend/micro-app/)
- [平台自定义登录页集成指南](../guide/advance/extend-frontend/micro-app/custom-login-integration)
- [布局组件](../guide/advance/extend-frontend/layout-component/)
- [组件库](../guide/advance/extend-frontend/amis-component/)

## 后端扩展专题

- [创建后端扩展包](./backend-extension-packages)
- [开发模块与 Maven 脚手架](./development-module-scaffold-and-maven-skeleton)
- [权限、主体与访问控制设计](./authority-subject-and-access-control-design)
- [扩展字段](../guide/advance/extend-backend/extend-field/)
- [扩展表达式](../guide/advance/extend-backend/extend-expression/)
- [扩展脚本](../guide/advance/extend-backend/extend-script/)
- [扩展逻辑流](../guide/advance/extend-backend/extend-logicflow/)

## 详细实现参考

- [高级指南总览](../guide/advance/)
- [扩展前端](../guide/advance/extend-frontend/)
- [扩展后端](../guide/advance/extend-backend/)
- [权限与访问控制](../guide/advance/authority-and-access-control)

## 阅读方式

- 先用总览、扩展点和协同模式判断是否真的需要写代码
- 再按前端扩展或后端扩展进入具体实现页
- 如果你当前目标还是交付标准业务功能，建议优先回到 [低代码开发](../low-code/)
