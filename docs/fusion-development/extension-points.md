---
title: 平台扩展点总表
sidebar_position: 4
---

# 平台扩展点总表

在进入具体扩展点之前，建议先确认平台是否已经提供了可复用的内建能力，例如调度、消息队列、WebSocket、文件上传、文档管理、Widget 或平台组件库。相关盘点见 [平台能力地图](../reference/platform-capability-map)。

这页的作用不是替代各专题细节，而是先帮你把入口选对。

## 先做一个总判断

| 你的目标 | 优先进入哪里 |
| ---- | ---- |
| 主要改页面、登录体验、布局或组件 | 前端扩展点 |
| 主要补运行时能力、上下文、节点或权限模型 | 后端扩展点 |
| 主要补开发平台中的一种可管理模型 | [开发模块与 Maven 脚手架](./development-module-scaffold-and-maven-skeleton) |
| 还不确定要不要写代码 | [何时用低代码，何时写代码](./when-to-use-code) |

## 前端扩展点

- 微前端应用：承接复杂页面或独立子应用
- 自定义登录页：替换默认登录体验
- 布局组件：替换顶栏、侧栏等基础布局
- 组件库：补充低代码页面里的复用前端组件能力

如果你当前要做的是登录入口替换，而不只是普通页面微前端，建议继续看 [自定义登录页与认证接入](./custom-login-page-and-auth-integration)。

如果你当前还在“微前端页面、布局组件、登录页、组件库、平台组件库”之间做判断，建议继续看 [前端融合开发方式](./frontend-extension-paths)。

## 常见“不一定要扩展”的场景

- 只是想补一个工作台首页、数据看板或快捷入口时，先评估 Widget 和用户仪表板能力
- 只是想分发一组前端组件给多个应用复用时，先评估平台组件库能力
- 只是想接一个实时状态推送或异步处理链路时，先评估 WebSocket、消息队列和调度能力

如果你正好在这几种场景里做判断，可以直接看 [工作台、Widget 与平台组件库](./workbench-widgets-and-component-libraries)。

## 后端扩展点

- 字段扩展：补充新的字段类型与行为
- 表达式扩展：补充新的表达式能力
- 脚本扩展：补充脚本上下文与执行能力
- 逻辑流扩展：补充新的逻辑流节点
- 权限与主体扩展：补充权限定义、主体来源、Claims 聚合与访问控制能力

## 后端扩展点怎么选

| 需求特征 | 更适合的入口 |
| ---- | ---- |
| 想让建模人员多选一个可复用字段类型 | [扩展字段](../guide/advance/extend-backend/extend-field/) |
| 想让 `${...}` 里直接多一个全局对象或工具方法 | [扩展表达式](../guide/advance/extend-backend/extend-expression/) |
| 想让脚本里直接多一个上下文对象，或补一类脚本执行能力 | [扩展脚本](../guide/advance/extend-backend/extend-script/) |
| 想让逻辑流编辑器里多一个可复用节点 | [扩展逻辑流](../guide/advance/extend-backend/extend-logicflow/) |
| 想补用户、主体、Claims、字段级控制和数据过滤 | [权限、主体与访问控制设计](./authority-subject-and-access-control-design) |

如果你当前还卡在“能力应该怎么打包、怎么装配、怎么做成开发平台模块”，建议继续看 [创建后端扩展包](./backend-extension-packages) 和 [开发模块与 Maven 脚手架](./development-module-scaffold-and-maven-skeleton)。

如果你当前要处理的是用户、主体、Claims、字段级控制或数据过滤，而不是普通业务角色配置，建议继续看 [权限、主体与访问控制设计](./authority-subject-and-access-control-design)。

## 两类常见误判

### 误判 1：其实已有能力，不必扩展

例如：

- 只是要做标准异步调度，其实先看调度能力
- 只是要发消息，其实先看通知模板和消息能力
- 只是要做工作台入口，其实先看 Widget 和用户仪表板

### 误判 2：已经是扩展问题，却还在配置层硬拧

例如：

- 想给所有表达式补一个统一 helper，却还在每个配置里复制逻辑
- 想做新字段语义，却还在单个模型里手工重复配置
- 想把复杂处理沉淀成节点，却一直堆脚本

## 推荐推进顺序

1. 先用这页确认扩展大类。
2. 再进入对应专题看最小实现和验证方式。
3. 如果最终发现要做的是独立 `*-dev` 模块，再转到脚手架文档。

## 详细实现参考

- [扩展前端](../guide/advance/extend-frontend/)
- [扩展后端](../guide/advance/extend-backend/)
- [权限、主体与访问控制设计](./authority-subject-and-access-control-design)
