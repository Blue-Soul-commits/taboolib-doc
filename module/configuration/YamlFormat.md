# YamlFormat
## 基本信息
- 类名和包路径: taboolib.module.configuration.YamlFormat
- 基本用途: 实现 NightConfig 库的 ConfigFormat 接口，为 YAML 配置格式提供支持
- 类型: 工具类
- 所属模块: basic-configuration

## 类结构
### 公开静态字段
> INSTANCE: YamlFormat -> 单例实例，用于全局访问 YamlFormat

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> 无类内可被访问字段

### 类方法
> createWriter(): ConfigWriter -> 创建 YAML 配置写入器，返回 YamlWriter 实例
> createParser(): ConfigParser<CommentedConfig> -> 创建 YAML 配置解析器，返回 YamlParser 实例
> createConfig(mapCreator: Supplier<Map<String, Object>>): CommentedConfig -> 创建 YAML 配置对象
> supportsComments(): boolean -> 返回是否支持注释，始终返回 true
> supportsType(type: Class<?>): boolean -> 检查是否支持指定的数据类型

## 实现细节
- 实现了 NightConfig 库的 ConfigFormat 接口，为 YAML 格式提供支持
- 作为单例模式实现，通过 INSTANCE 静态字段提供全局访问点
- 创建的 YamlWriter 和 YamlParser 实例负责 YAML 配置的读写操作
- 支持注释功能，使配置文件更易于理解和维护
- 支持多种数据类型，包括基本类型、集合类型和自定义配置类型
- 与 TabooLib 的配置系统紧密集成，是 Type.YAML 枚举值的底层实现

## 使用场景
> 在 TabooLib 的配置系统中作为 YAML 格式的核心实现
> 通过 Type.YAML 枚举值在配置系统中被引用
> 在 Configuration.empty() 等方法中用于创建空的 YAML 配置
> 在 ConfigFile 类中用于解析和写入 YAML 配置文件
> 在 ObjectConverter 中用于检查数据类型的兼容性

## 注意事项
> 依赖于 NightConfig 库（3.6.7 版本）和 SnakeYAML 库（2.2 版本）
> 通过 RuntimeDependency 注解确保正确的依赖版本被加载
> 支持的数据类型在 supportsType 方法中明确定义
> 作为单例使用，不应创建多个实例
> 与 YamlParser 和 YamlWriter 配合使用，共同构成 YAML 处理系统

