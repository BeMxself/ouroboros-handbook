---
sidebar_position: 5
---

# WebAPI 模型

适用对象：需要对外提供接口的低代码开发人员、集成开发人员和后端扩展开发人员。

WebAPI 模型用于统一描述 HTTP 接口契约，包括请求方式、路径、参数、响应结构以及接口的实际处理适配方式。它让“接口长什么样”和“接口由谁执行”可以分开管理。

## 它解决什么问题

- 统一管理接口契约，减少接口散落在代码和页面配置里的情况
- 让标准接口、逻辑流接口和代码扩展接口使用一致的模型描述
- 让权限控制、页面调用和外部集成都围绕稳定的 API 契约协同

## 核心组成

- 请求定义：HTTP 方法、路径、入参、请求体和响应体
- 错误语义：异常、状态码、返回格式
- 处理适配器：接口由哪种运行时能力来处理
- 访问控制：与 [权限模型](../authority-model/) 和业务安全规则协同

在当前实现中，高代码 Spring MVC 接口也会在 `RequestMapping` 注册阶段被拦截并抽取成 `WebAPIModel`。这意味着参数、请求体、响应、Swagger 注解说明和常见 `javax.validation` 约束，会和低代码接口一样统一沉淀到 WebAPI 契约层。

运行时还可以把这些统一后的契约直接导出为 OpenAPI 3.1 文档：

- 导出入口：`/api/sys/webapi/openapi.json`
- 默认包含当前应用中全部已注册的高代码和低代码 `WebAPIModel`
- 支持按 `scope`、`handlerType`、`tag`、`pathPrefix`、`api` 等条件过滤
- 返回原生 OpenAPI JSON，而不是平台 `WebApiResult` 包装

## 常见适配方式

- `RequestMapping`：直接对接 Spring Web MVC
- `RouterFunction`：对接响应式风格处理
- [逻辑流模型](../logicflow-model/)：通过低代码流程处理接口逻辑
- 自定义代码扩展：在融合开发场景下提供专用处理能力

其中 `RequestMapping` 适配已经不再只保留路由标识，而是会补齐 OpenAPI 3.1 操作级元数据，为后续统一生成 Swagger 文档或 JSON 定义提供基础。

## 与其他模型的关系

- [业务模型](../business-model/) 常会投射出标准 WebAPI
- [UI 模型](../ui-model/) 和 [UI Schema](../ui-schema/) 产生的页面通常会调用这些接口
- [逻辑流模型](../logicflow-model/) 可以作为接口实现层
- [权限模型](../authority-model/) 决定接口是否可被访问

## 阅读建议

- 规范与查阅请看 [Web API 规范](../../api/web-api-spec/)
- 如果你想查具体能力，请从 [API 参考](../../api/) 进入
