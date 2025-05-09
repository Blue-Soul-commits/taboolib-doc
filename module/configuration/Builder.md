# Builder
## 基本信息
- 类名和包路径: taboolib.module.configuration.util.Builder
- 基本用途: 提供创建配置对象的便捷构建器函数
- 类型: 文件 (包含顶层函数)
- 所属模块: basic-configuration

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> newConfig(type: Type = Type.YAML, concurrent: Boolean = true, builder: Configuration.() -> Unit): Configuration -> 创建一个新的配置对象
> newJsonConfig(concurrent: Boolean = true, builder: Configuration.() -> Unit): Configuration -> 创建一个新的 JSON 配置对象

### 类内可被访问字段
> 无

### 类方法
> 无

## 实现细节
- 提供了两个顶层函数，用于简化配置对象的创建和初始化
- 使用 Kotlin 的函数类型和接收者，允许在 lambda 表达式中直接操作配置对象
- newConfig 函数支持指定配置类型和并发模式，默认为 YAML 格式和并发模式
- newJsonConfig 函数是 newConfig 的特化版本，固定使用 JSON_MINIMAL 格式
- 两个函数都使用 Configuration.empty() 创建空配置，然后应用构建器函数

## 使用场景
> 快速创建和初始化配置对象
> 使用 DSL 风格的语法构建配置
> 在代码中动态生成配置
> 创建临时配置对象用于数据处理

## 注意事项
> 默认使用并发模式 (concurrent = true)，适合多线程环境
> 构建器函数在配置对象上下文中执行，可以直接使用 Configuration 的方法
> 这些函数创建的是内存中的配置对象，需要手动保存到文件
> newJsonConfig 使用 JSON_MINIMAL 格式，生成的 JSON 更紧凑

