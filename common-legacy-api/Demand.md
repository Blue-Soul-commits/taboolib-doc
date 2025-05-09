# Demand
## 基本信息
- 类名和包路径: taboolib.common5.Demand
- 基本用途: 命令行风格的字符串解析工具，将格式化字符串解析为结构化数据
- 类型: 数据解析类
- 所属模块: common5-legacy-api

## 类结构
### 公开静态方法
> String.toDemand(): Demand -> 将字符串转换为 Demand 对象的扩展函数

### 类内可被访问字段
> source: String -> 原始输入字符串
> namespace: String -> 命令的命名空间（第一个参数）
> dataMap: HashMap<String, String> -> 存储键值对的映射
> args: ArrayList<String> -> 存储普通参数的列表
> tags: ArrayList<String> -> 存储标签的列表

### 类方法
> get(key: List<String>, def: String? = null): String? -> 从多个可能的键中获取第一个非空值，如果都为空则返回默认值
> get(key: String, def: String? = null): String? -> 获取指定键的值，如果不存在则返回默认值
> get(index: Int, def: String? = null): String? -> 获取指定索引的普通参数，如果不存在则返回默认值
> getInt(key: String, def: Int = 0): Int -> 获取指定键的整数值，如果不存在或转换失败则返回默认值
> getDouble(key: String, def: Double = 0.0): Double -> 获取指定键的浮点数值，如果不存在或转换失败则返回默认值
> getBoolean(key: String, def: Boolean = false): Boolean -> 获取指定键的布尔值，如果不存在或转换失败则返回默认值
> containsKey(key: String): Boolean -> 检查是否包含指定键
> containsTag(tag: String): Boolean -> 检查是否包含指定标签

## 实现细节
- 使用状态机模式解析输入字符串，通过 ParseState 枚举定义三种解析状态：NORMAL（普通状态）、IN_QUOTES（在引号内）和 AFTER_KEY（键之后）
- 支持处理带引号的参数，允许包含空格的字符串作为单个参数
- 支持使用反斜杠转义引号，如 \"
- 处理未闭合的引号和未赋值的键的特殊情况
- 使用 Kotlin 的扩展属性（cint、cdouble、cbool）进行类型转换
- 提供了 equals、hashCode 和 toString 方法的完整实现

## 使用场景
> 命令行参数解析
> 游戏内命令系统
> 配置字符串解析
> 用户输入处理
> API 参数解析

## 注意事项
> 空字符串会被解析为空命名空间
> 未赋值的键会被设置为空字符串
> 未闭合的引号会被视为字符串的结束
> 类型转换失败时会返回默认值，而不是抛出异常
> 参数解析是在构造函数中完成的，不需要显式调用 parse 方法
