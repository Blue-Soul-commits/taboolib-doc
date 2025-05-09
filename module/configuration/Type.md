# Type
## 基本信息
- 类名和包路径: taboolib.module.configuration.Type
- 基本用途: 定义配置文件的格式类型，提供不同格式的配置实现
- 类型: 枚举类 (Enum Class)
- 所属模块: basic-configuration

## 类结构
### 公开静态字段
> YAML -> YAML 格式配置
> TOML -> TOML 格式配置
> JSON -> JSON 格式配置（标准格式）
> JSON_MINIMAL -> JSON 格式配置（最小化格式）
> HOCON -> HOCON 格式配置
> FAST_JSON -> JSON 格式配置（最小化格式，已废弃）

### 公开静态方法
> getType(format: ConfigFormat<*>): Type -> 根据 ConfigFormat 对象获取对应的 Type 枚举值

### 类内可被访问字段
> format: () -> ConfigFormat<out Config> -> 返回对应格式的 ConfigFormat 对象的函数（私有）

### 类方法
> newFormat(): ConfigFormat<out Config> -> 创建并返回对应格式的 ConfigFormat 对象

## 实现细节
- 使用 NightConfig 库作为底层配置实现
- 支持多种配置格式：YAML、TOML、JSON、HOCON
- 在静态初始化块中设置系统属性 "nightconfig.preserveInsertionOrder" 为 "true"，保持配置项的插入顺序
- 每个枚举值都关联一个返回 ConfigFormat 对象的函数，通过 newFormat() 方法调用
- 提供 getType() 方法，用于根据 ConfigFormat 对象反向查找对应的 Type 枚举值

## 使用场景
> 指定配置文件的格式类型
> 创建特定格式的配置对象
> 在不同格式之间转换配置
> 根据文件扩展名自动选择配置格式

## 注意事项
> FAST_JSON 已被废弃，建议使用 JSON_MINIMAL 代替
> 不同格式的配置有不同的特性和限制，如 YAML 支持注释而标准 JSON 不支持
> 配置项的插入顺序会被保留，这对于某些需要顺序的配置很重要
> YAML 格式使用自定义的 YamlFormat 实现，而不是 NightConfig 的标准实现

