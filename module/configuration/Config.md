# Config
## 基本信息
- 类名和包路径: taboolib.module.configuration.Config
- 基本用途: 用于标记配置文件字段，自动加载和绑定配置文件到字段
- 类型: 注解类 (Annotation Class)
- 所属模块: basic-configuration

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> value: String -> 配置文件名称，默认为 "config.yml"
> target: String -> 目标文件路径，默认为空字符串
> migrate: Boolean -> 是否迁移配置，默认为 false
> autoReload: Boolean -> 是否自动重载，默认为 false
> concurrent: Boolean -> 是否支持并发访问，默认为 true

### 类方法
> 无

## 实现细节
- 这是一个运行时注解 (@Retention(AnnotationRetention.RUNTIME))
- 只能应用于字段 (@Target(AnnotationTarget.FIELD))
- 通过 ConfigLoader 类在初始化阶段自动处理带有此注解的字段
- 当 autoReload 设置为 true 时，会监听文件变更并自动重新加载配置
- 当 concurrent 设置为 true 时，会使用支持并发的配置实现

## 使用场景
> 在类中声明配置文件字段，自动加载和绑定配置文件
> 实现配置文件的自动重载功能
> 在模块初始化时自动加载配置文件

## 注意事项
> 被注解的字段类型应该是 Configuration 或其子类
> 如果 target 为空，则使用 value 作为目标文件路径
> 当 autoReload 为 true 时，会增加文件系统监听器的开销

