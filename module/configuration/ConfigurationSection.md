# ConfigurationSection
## 基本信息
- 类名和包路径: taboolib.library.configuration.ConfigurationSection
- 基本用途: 提供对配置文件中节点的访问和操作，支持多种数据类型和嵌套结构
- 类型: 接口
- 所属模块: basic-configuration

## 类结构
### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> primitiveConfig: Any -> 原始配置对象
> parent: ConfigurationSection? -> 父节点
> name: String -> 节点名称
> type: Type -> 节点类型，表示配置格式（YAML、JSON、TOML等）

### 类方法
> getKeys(deep: Boolean): Set<String> -> 获取此节点中所有键的集合
> contains(path: String): Boolean -> 检查此节点是否包含给定路径
> isSet(path: String): Boolean -> 同 contains 方法，一个别名
> get(path: String): Any? -> 通过路径获取请求的对象
> get(path: String, def: Any?): Any? -> 通过路径获取请求的对象，如果未找到则返回默认值
> set(path: String, value: Any?) -> 将指定路径设置为给定值
> getString(path: String): String? -> 获取字符串值
> getString(path: String, def: String?): String? -> 获取字符串值，如果未找到则返回默认值
> isString(path: String): Boolean -> 检查指定路径是否为字符串
> getInt(path: String): Int -> 获取整数值
> getInt(path: String, def: Int): Int -> 获取整数值，如果未找到则返回默认值
> isInt(path: String): Boolean -> 检查指定路径是否为整数
> getBoolean(path: String): Boolean -> 获取布尔值
> getBoolean(path: String, def: Boolean): Boolean -> 获取布尔值，如果未找到则返回默认值
> isBoolean(path: String): Boolean -> 检查指定路径是否为布尔值
> getDouble(path: String): Double -> 获取双精度浮点数值
> getDouble(path: String, def: Double): Double -> 获取双精度浮点数值，如果未找到则返回默认值
> isDouble(path: String): Boolean -> 检查指定路径是否为双精度浮点数
> getLong(path: String): Long -> 获取长整数值
> getLong(path: String, def: Long): Long -> 获取长整数值，如果未找到则返回默认值
> isLong(path: String): Boolean -> 检查指定路径是否为长整数
> getList(path: String): List<*>? -> 获取列表值
> getList(path: String, def: List<*>?): List<*>? -> 获取列表值，如果未找到则返回默认值
> isList(path: String): Boolean -> 检查指定路径是否为列表
> getStringList(path: String): List<String> -> 获取字符串列表
> getIntegerList(path: String): List<Int> -> 获取整数列表
> getBooleanList(path: String): List<Boolean> -> 获取布尔值列表
> getDoubleList(path: String): List<Double> -> 获取双精度浮点数列表
> getFloatList(path: String): List<Float> -> 获取浮点数列表
> getLongList(path: String): List<Long> -> 获取长整数列表
> getByteList(path: String): List<Byte> -> 获取字节列表
> getCharacterList(path: String): List<Char> -> 获取字符列表
> getShortList(path: String): List<Short> -> 获取短整数列表
> getMapList(path: String): List<Map<*, *>> -> 获取映射列表
> getConfigurationSection(path: String): ConfigurationSection? -> 获取配置节点
> isConfigurationSection(path: String): Boolean -> 检查指定路径是否为配置节点
> getEnum(path: String, type: Class<T>): T? -> 获取枚举值
> getEnumList(path: String, type: Class<T>): List<T> -> 获取枚举列表
> createSection(path: String): ConfigurationSection -> 创建新的配置节点
> toMap(): Map<String, Any?> -> 将当前配置节点转换为 Map
> getComment(path: String): String? -> 获取指定路径的注释
> getComments(path: String): List<String> -> 获取指定路径的注释列表
> setComment(path: String, comment: String?) -> 设置指定路径的注释
> setComments(path: String, comments: List<String>) -> 设置指定路径的注释列表
> addComments(path: String, comments: List<String>) -> 向指定路径添加注释
> getValues(deep: Boolean): Map<String, Any?> -> 获取当前配置节点的所有值
> clear() -> 清除当前配置节点中的所有值

## 实现细节
- 作为 TabooLib 配置系统的核心接口，定义了配置节点的基本操作
- 支持多种数据类型的读取和写入，包括基本类型、集合类型和自定义类型
- 支持嵌套结构，可以通过点分隔的路径访问深层次的配置项
- 支持注释的读取和写入，增强配置文件的可读性
- 提供类型检查方法，可以验证配置项的数据类型
- 支持默认值，当配置项不存在时返回指定的默认值
- 支持枚举类型的读取和写入，方便使用枚举常量
- 在 ConfigSection 类中实现，该类是 ConfigurationSection 接口的主要实现
- 在 ConfigFile 类中扩展，增加了文件操作相关的功能

## 使用场景
> 读取和修改配置文件中的各种数据
> 创建和管理嵌套的配置结构
> 处理带有注释的配置文件
> 在插件开发中用于存储和读取设置
> 与 @Config 注解配合使用，自动加载和管理配置文件
> 与 @ConfigNode 注解配合使用，将配置值绑定到字段
> 支持多种配置格式，如 YAML、JSON、TOML 和 HOCON

## 注意事项
> 路径使用点号（.）分隔层级，例如 "section.key"
> 当使用 get 方法获取不存在的路径时，返回 null 或指定的默认值
> 当使用 set 方法设置 null 值时，会删除该路径的配置项
> 使用 getConfigurationSection 方法获取子节点时，如果路径不存在则返回 null
> 使用 createSection 方法可以创建新的子节点，如果路径已存在则会覆盖
> 注释功能仅在支持注释的配置格式（如 YAML）中有效
> 在处理列表类型时，会尝试将值转换为指定类型，不兼容的值会被忽略

