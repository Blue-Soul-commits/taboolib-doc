# ConfigSection
## 基本信息
- 类名和包路径: taboolib.module.configuration.ConfigSection
- 基本用途: 实现配置节点的核心功能，提供配置数据的读写、转换和操作
- 类型: 类 (Class)
- 所属模块: basic-configuration

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> unwrap(v: Any?): Any? -> 解包配置值，转换为原始类型或 Map
> unwrap(list: List<*>, parent: ConfigSection): List<*> -> 解包列表中的配置值

### 类内可被访问字段
> root: Config -> 底层的 NightConfig 配置对象
> name: String -> 配置节点的名称
> parent: ConfigurationSection? -> 父配置节点
> configType: Type -> 配置类型（私有）
> primitiveConfig: Any -> 底层配置对象
> type: Type -> 配置类型

### 类方法
> getKeys(deep: Boolean): Set<String> -> 获取所有键，deep 为 true 时包含子节点
> contains(path: String): Boolean -> 检查路径是否存在
> isSet(path: String): Boolean -> 检查路径是否设置
> get(path: String): Any? -> 获取指定路径的值
> get(path: String, def: Any?): Any? -> 获取指定路径的值，不存在时返回默认值
> set(path: String, value: Any?) -> 设置指定路径的值
> getString(path: String): String? -> 获取字符串值
> getString(path: String, def: String?): String? -> 获取字符串值，不存在时返回默认值
> isString(path: String): Boolean -> 检查值是否为字符串
> getInt(path: String): Int -> 获取整数值
> getInt(path: String, def: Int): Int -> 获取整数值，不存在时返回默认值
> isInt(path: String): Boolean -> 检查值是否为整数
> getBoolean(path: String): Boolean -> 获取布尔值
> getBoolean(path: String, def: Boolean): Boolean -> 获取布尔值，不存在时返回默认值
> isBoolean(path: String): Boolean -> 检查值是否为布尔值
> getDouble(path: String): Double -> 获取双精度浮点值
> getDouble(path: String, def: Double): Double -> 获取双精度浮点值，不存在时返回默认值
> isDouble(path: String): Boolean -> 检查值是否为双精度浮点值
> getLong(path: String): Long -> 获取长整数值
> getLong(path: String, def: Long): Long -> 获取长整数值，不存在时返回默认值
> isLong(path: String): Boolean -> 检查值是否为长整数
> getList(path: String): List<*>? -> 获取列表值
> getList(path: String, def: List<*>?): List<*>? -> 获取列表值，不存在时返回默认值
> isList(path: String): Boolean -> 检查值是否为列表
> getStringList(path: String): List<String> -> 获取字符串列表
> getIntegerList(path: String): List<Int> -> 获取整数列表
> getBooleanList(path: String): List<Boolean> -> 获取布尔值列表
> getDoubleList(path: String): List<Double> -> 获取双精度浮点列表
> getFloatList(path: String): List<Float> -> 获取单精度浮点列表
> getLongList(path: String): List<Long> -> 获取长整数列表
> getByteList(path: String): List<Byte> -> 获取字节列表
> getCharacterList(path: String): List<Char> -> 获取字符列表
> getShortList(path: String): List<Short> -> 获取短整数列表
> getMapList(path: String): List<Map<*, *>> -> 获取映射列表
> getConfigurationSection(path: String): ConfigurationSection? -> 获取配置节点
> isConfigurationSection(path: String): Boolean -> 检查值是否为配置节点
> getEnum<T : Enum<T>>(path: String, type: Class<T>): T? -> 获取枚举值
> getEnumList<T : Enum<T>>(path: String, type: Class<T>): List<T> -> 获取枚举列表
> createSection(path: String): ConfigurationSection -> 创建新的配置节点
> toMap(): Map<String, Any?> -> 将配置节点转换为 Map
> getComment(path: String): String? -> 获取注释
> getComments(path: String): List<String> -> 获取多行注释
> setComment(path: String, comment: String?) -> 设置注释
> setComments(path: String, comments: List<String>) -> 设置多行注释
> addComments(path: String, comments: List<String>) -> 添加多行注释
> getValues(deep: Boolean): Map<String, Any?> -> 获取所有值
> toString(): String -> 将配置转换为字符串
> clear() -> 清空配置

## 实现细节
- 实现了 ConfigurationSection 接口，提供了配置节点的核心功能
- 使用 NightConfig 库的 Config 对象作为底层实现
- 支持嵌套的配置节点结构，通过点分隔的路径访问
- 支持各种数据类型的读写和转换，包括基本类型、列表、映射和枚举
- 支持配置注释的读写，通过 CommentedConfig 接口
- 提供了特殊值处理："~"和"null"转换为 null，"''"和"\"\""转换为空字符串
- 支持 Unicode 编码的字符串自动解码
- 支持通过 Commented 和 CommentedList 类添加带注释的值

## 使用场景
> 作为 TabooLib 配置系统的核心实现类
> 读取和修改配置文件中的各种类型的值
> 创建和操作嵌套的配置结构
> 处理带注释的配置项
> 将配置数据转换为 Map 或字符串

## 注意事项
> 路径使用点号（.）分隔层级，例如 "database.host"
> 空路径（""）返回当前节点本身
> 支持特殊值处理："~"和"null"转换为 null，"''"和"\"\""转换为空字符串
> 在获取不存在的路径时，基本类型方法会返回默认值或类型的零值
> 列表类型方法在路径不存在时返回空列表，而不是 null
> 注释功能仅在底层配置支持注释时可用（如 YAML、TOML）

