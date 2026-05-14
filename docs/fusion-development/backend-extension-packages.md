---
title: 创建后端扩展包
sidebar_position: 7
---

# 创建后端扩展包

这页适合已经确认要通过代码给潮汐栈补充后端能力的专业开发者。

在潮汐栈里，很多后端扩展不是直接改平台主工程，而是做成一个可安装、可装配的扩展包。它通常更接近一个 Spring Boot Starter 风格的能力包，而不是单纯的工具类集合。

## 什么时候应该做成后端扩展包

- 需要补新的字段、表达式、脚本上下文或逻辑流节点
- 需要把某项集成能力做成可复用运行时能力
- 需要让多个应用或多个场景共用同一套后端扩展
- 希望扩展结果可以被平台统一装配，而不是散落在业务代码里

如果只是单个业务里的临时逻辑，通常先评估配置、脚本或现成节点是否已经足够。

## 先判断你做的是哪种扩展包

### 纯资源 / 纯 SPI 扩展包

适合这类场景：

- 只提供字段模板资源
- 只注册 `ELContextWrapper` / `ScriptContextWrapper` / `NodeBuilder`
- 不需要额外 Spring Bean 和自动装配

这种包的重点是资源文件和 `META-INF/services/*`。

### Starter 风格扩展包

适合这类场景：

- 扩展能力依赖 Spring Bean
- 需要自动装配配置类
- 需要把多个 SPI、资源和 Bean 作为一个完整能力分发

这种包除了 SPI，还通常要补：

- 自动装配类
- `META-INF/spring.factories`
- 依赖管理

多数真正可复用的后端能力包，最后都会长成这一类。

## 先理解后端扩展包的最小形态

一个典型的后端扩展包，至少会包含下面几类东西：

- Maven 模块与 `pom.xml`
- 自动装配类
- `META-INF/spring.factories`
- 按需要补充的 SPI 注册文件
- 按需要补充的 `META-INF/ouroboros/*` 资源声明

也就是说，它的关键不只是“写了一个 Bean”，而是要让平台知道：

- 启动时该怎么装配它
- 运行时该怎么发现它
- 哪些模型、资源或扩展点会消费它

一个常见骨架大致会长这样：

```text
my-capability/
├── pom.xml
└── src/main/
    ├── java/com/example/mycapability/
    │   ├── MyCapabilityAutoConfiguration.java
    │   └── ...能力实现...
    └── resources/
        └── META-INF/
            ├── spring.factories
            ├── services/
            │   ├── com.ouroboros.expression.ELContextWrapper
            │   ├── com.ouroboros.script.ScriptContextWrapper
            │   └── com.ouroboros.logicflow.nodes.NodeBuilder
            └── ouroboros/
                └── field-types/
```

并不是每个扩展包都要同时具备这些文件，但你做的那类能力需要什么，就必须把那一层闭环补全。

## 常见扩展落点怎么选

### 字段扩展

适合补新的字段类型、字段模板和字段行为。

常见抓手是：

- 字段类型资源
- `FieldTypeDefinitionProvider`

### 表达式扩展

适合给 `${...}` 表达式注入新的全局变量、工具对象或上下文能力。

常见抓手是：

- `ELContextWrapper`
- `META-INF/services/com.ouroboros.expression.ELContextWrapper`

### 脚本扩展

适合给脚本运行时补新的上下文对象或工具能力。

常见抓手是：

- `ScriptContextWrapper`

### 逻辑流扩展

适合补新的逻辑流节点，让业务开发者在可视化编排里直接用。

常见抓手是：

- `NodeBuilder`
- `META-INF/services/com.ouroboros.logicflow.nodes.NodeBuilder`

## 自动装配和 SPI 分别解决什么问题

很多第一次做扩展包的人会把这两件事混在一起：

- `spring.factories` 解决的是“Spring 启动时要不要把这批 Bean 装起来”
- `META-INF/services/*` 解决的是“平台扩展点在运行时能不能发现这类实现”

它们经常同时出现，但并不等价。

例如：

- 一个字段类型资源包可能几乎不需要 Spring Bean，但需要资源路径和 `FieldTypeDefinitionProvider`。
- 一个配置能力节点包可能既要自动装配拿到 `ConfigurationService`，又要注册 `NodeBuilder`。

## 为什么扩展包通常长得像 Starter

因为潮汐栈的大量运行时能力，都是围绕自动装配和 SPI 发现接起来的。

这意味着一个扩展包通常至少要解决两件事：

1. 容器启动时，哪些 Bean 要被自动装上
2. 平台运行时，哪些 SPI 或资源要被统一发现

如果只有代码实现，没有装配和注册，平台往往“编译没问题，但能力看不见”。

## 一个推荐的交付顺序

1. 先明确扩展点属于字段、表达式、脚本、逻辑流还是开发模块。
2. 建一个独立 Maven 模块，先把依赖和包名结构稳定下来。
3. 写最小能力实现，例如一个 wrapper、一个 builder 或一个字段模板。
4. 补 `META-INF/services/*` 和必要的 `META-INF/ouroboros/*` 资源。
5. 如果依赖 Spring Bean，再补自动装配类和 `spring.factories`。
6. 在目标运行环境安装后做最小验证。
7. 最后再补复杂参数、更多节点或更多资源。

## 一个很常见的坑

扩展包中的 Spring Bean 没有被加载，很多时候不是代码本身错了，而是：

- 没有 `META-INF/spring.factories`
- `EnableAutoConfiguration` 没配对
- 其他 Starter 的 `spring.factories` 覆盖了当前扩展包

这也是为什么后端扩展包的排查，不应该只盯着业务代码，而要把装配结构一起看。

除此之外，还有几类高频问题：

- SPI 文件路径正确，但里面写错了实现类全限定名。
- 字段模板、节点资源等放错了 `META-INF/ouroboros/*` 路径。
- 扩展包已经安装，但实际运行的应用并没有引用或启用对应能力。
- 后端扩展已生效，但开发平台侧没有相应 UI 入口，团队仍然觉得“不可用”。

## 一个实用的检查顺序

当你写完一个后端扩展包后，至少建议按下面顺序验证：

1. 扩展包是否已经被正确安装到当前运行环境
2. 自动装配类是否通过 `spring.factories` 被注册
3. 需要的 SPI 文件是否已经补齐
4. 需要的资源文件是否已经放到正确的 `META-INF` 目录
5. 页面、模型、脚本、流程或配置是否真的引用到了这个扩展能力

这样比只看“代码有没有编译通过”更有用。

## 和开发模块脚手架的区别

后端扩展包主要解决的是“运行时能力怎么扩展”。

如果你要做的是开发平台里的 `*-dev` 模块，例如模型管理、VCS 提交、锁定、开发态 CRUD 和片段页面，那更适合看开发模块脚手架，而不是普通运行时扩展包。

一个简单判断方式是：

- 你要补的是“运行时能力” -> 看这页
- 你要补的是“开发平台里可管理的一类模型” -> 看脚手架页

## 推荐阅读顺序

1. 先看 [扩展后端](../guide/advance/extend-backend/)
2. 再按能力类型进入 [扩展字段](../guide/advance/extend-backend/extend-field/)、[扩展表达式](../guide/advance/extend-backend/extend-expression/)、[扩展脚本](../guide/advance/extend-backend/extend-script/)、[扩展逻辑流](../guide/advance/extend-backend/extend-logicflow/)
3. 遇到装配问题时，再回看 [后端 FAQ](../faq/backend/)

## 下一步看哪里

- 想继续看开发平台模块骨架：看 [开发模块与 Maven 脚手架](./development-module-scaffold-and-maven-skeleton)
- 想先判断是否真的需要写代码：看 [何时用低代码，何时写代码](./when-to-use-code)
- 想直接进入具体扩展点：看 [扩展后端](../guide/advance/extend-backend/)
