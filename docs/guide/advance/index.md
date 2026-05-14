---
sidebar_position: 100
---

# 高级

这里保留的是历史高级主题入口。当前建议优先从 [融合开发](../../fusion-development/) 主线进入，再按需要回到本目录查阅具体实现细节。

本目录主要承担“详细实现参考”的作用，不再作为判断是否需要写代码的第一入口。更直接地说：这里解决的是“已经决定要扩展，具体怎么做”，而不是“要不要扩展”。

## 建议优先阅读

1. [融合开发入口](../../fusion-development/)
2. [扩展前端](./extend-frontend/)
3. [扩展后端](./extend-backend/)
4. [权限、主体与访问控制设计](../../fusion-development/authority-subject-and-access-control-design)
5. [权限与访问控制](./authority-and-access-control)

## 这目录适合什么时候用

当你已经明确遇到下面这类问题时，这里会比总览页更直接：

- 前端页面、登录页、布局或组件需要自定义
- 后端字段、表达式、脚本、逻辑流节点需要扩展
- 权限、主体、Claims 和访问控制已经超出普通 RBAC 配置
- 你需要查某个具体扩展入口的接入方式，而不是继续做路线判断

如果你当前还在判断“到底该不该写代码”，优先回到 [融合开发](../../fusion-development/)。

## 详细实现专题

- [扩展前端](./extend-frontend/)
- [扩展后端](./extend-backend/)
- [AMIS 开发参考](./amis-reference/)
- [权限、主体与访问控制设计](../../fusion-development/authority-subject-and-access-control-design)
- [权限与访问控制](./authority-and-access-control)

## 目录和主线怎么对应

| 详细实现专题 | 更适合解决什么问题 | 对应主线入口 |
| ------------ | ------------------ | ------------ |
| 扩展前端 | 微前端页面、布局组件、组件库、自定义登录页 | [前端融合开发方式](../../fusion-development/frontend-extension-paths) |
| 扩展后端 | 字段、表达式、脚本、逻辑流节点等平台扩展 | [平台扩展点总表](../../fusion-development/extension-points) |
| AMIS 开发参考 | AMIS 官方能力和平台前端能力如何配合使用 | [页面交付：标准页面、动态表单与 UI Schema](../../low-code/page-delivery-with-dynamic-forms-and-ui-schema) |
| 权限与访问控制 | 访问控制的实现方式、接口和扩展边界 | [权限、主体与访问控制设计](../../fusion-development/authority-subject-and-access-control-design) |

## 一条推荐阅读顺序

大多数专业开发场景，建议按下面顺序进入：

1. 先在 [融合开发](../../fusion-development/) 中确认是否真的需要代码扩展
2. 再用 [平台扩展点总表](../../fusion-development/extension-points) 定位到前端、后端还是权限扩展
3. 最后回到本目录查具体实现方式

这样可以避免直接扎进实现细节，却没有先判断扩展边界。

## 查阅方式

- 先在 [融合开发](../../fusion-development/) 中判断场景是否真的需要代码扩展
- 再进入这里查看前端扩展、后端扩展或访问控制的具体实现
- 如果需求仍能通过模型、配置和标准能力完成，优先回到 [低代码开发](../../low-code/)

## 下一步看哪里

- 想先做路线判断：看 [何时用低代码，何时写代码](../../fusion-development/when-to-use-code)
- 想直接看前端扩展：看 [扩展前端](./extend-frontend/)
- 想直接看后端扩展：看 [扩展后端](./extend-backend/)
- 想先看权限与访问控制实现：看 [权限与访问控制](./authority-and-access-control)
