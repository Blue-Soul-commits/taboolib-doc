# ConfigNode
## 基本信息
- 类名和包路径: taboolib.module.configuration.ConfigNode
- 基本用途: 用于标记配置节点，将配置文件中的特定节点绑定到字段、类或文件
- 类型: 注解类 (Annotation Class)
- 所属模块: basic-configuration

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> value: String -> 配置节点路径，默认为空字符串
> bind: String -> 绑定的配置文件名称，默认为 "config.yml"

### 类方法
> 无

## 实现细节
- 这是一个运行时注解 (@Retention(AnnotationRetention.RUNTIME))
- 可以应用于字段、类或文件 (@Target(AnnotationTarget.FIELD, AnnotationTarget.CLASS, AnnotationTarget.FILE))
- 通过 ConfigNodeLoader 类在初始化阶段自动处理带有此注解的元素
- 当应用于字段时，会将配置文件中指定节点的值绑定到该字段
- 当应用于类或文件时，可以为整个类或文件指定默认的配置绑定

## 使用场景
> 将配置文件中的特定节点绑定到类字段
> 为类中的多个字段指定默认的配置文件
> 实现配置节点与代码的自动映射
> 在配置重载时自动更新绑定的字段值

## 注意事项
> 如果 value 为空，则使用字段名称作为节点路径
> 如果在类级别使用此注解，则类中的所有 ConfigNode 注解如果未指定 bind 值，将使用类级别指定的配置文件
> 配置节点必须存在于指定的配置文件中，否则会产生警告
> 与 @Config 注解配合使用时，可以实现更复杂的配置绑定

