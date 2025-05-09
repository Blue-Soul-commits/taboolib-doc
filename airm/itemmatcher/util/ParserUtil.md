# ParserUtils

## 基本信息
- 类名和包路径: top.maplex.arim.tools.itemmatch.util.ParserUtils
- 基本用途: 物品匹配条件的解析工具类，提供将字符串条件转换为条件对象的功能
- 类型: 单例对象(object)
- 所属模块: 物品匹配工具模块

## 类结构

### 公开静态字段
> 无显式定义的公开静态字段

### 公开静态方法
> splitConditions(expression: String): List<String> -> 将复合表达式分割为单独的条件字符串
> parseKeyValue(condition: String): Pair<String, String>? -> 解析键值对条件
> parseStringCondition(value: String): MatchCondition.StringCondition -> 解析字符串条件
> parseListCondition(value: String): MatchCondition -> 解析复合列表条件
> parseNumberListCondition(value: String): MatchCondition -> 解析数值复合列表条件
> parseNumberCondition(value: String): MatchCondition.NumberCondition -> 解析数值条件
> parseNbt(input: String): Map<String, Any>? -> 解析NBT格式的键值对字符串

### 类内可被访问字段
> 无额外的类内可被访问字段

### 类方法
> 同公开静态方法

## 实现细节
- 使用Kotlin object单例模式实现，所有方法都是静态的
- 提供多种解析方法，支持不同的条件格式和复杂度：
  1. splitConditions: 处理多条件表达式，支持大括号内嵌套条件的情况
  2. parseKeyValue: 基本的键值对分割，以冒号(:)为分隔符
  3. parseStringCondition: 解析字符串操作条件，支持多种操作符和修饰符
  4. parseListCondition: 解析ANY/ALL/NONE逻辑组合的条件列表
  5. parseNumberCondition: 解析数值比较条件，支持前缀标签和比较运算符
  6. parseNbt: 解析NBT格式字符串为键值对Map
- 使用正则表达式进行复杂条件的模式匹配
- 支持多种字符串操作的简写形式，如contains/con/c等
- 支持条件修饰符，如uncolored/uc等
- 处理不同数据类型的自动转换，如字符串、整数、浮点数和布尔值

## 使用场景
> 解析配置文件或命令中的物品匹配条件字符串
> 为物品匹配系统提供统一的条件解析接口
> 支持复杂的条件组合和嵌套，实现高度灵活的匹配逻辑
> 在物品筛选、验证和比较功能中作为基础工具

## 注意事项
> 解析方法可能会抛出异常，使用时应考虑异常处理
> parseStringCondition在无法匹配指定模式时，会将整个输入视为EXACT匹配的值
> 解析方法中包含一些默认行为，如parseNumberCondition在无法解析时会返回等于0的条件
> 条件字符串必须遵循特定格式，否则可能导致解析错误或意外结果
> 复合条件支持嵌套，但嵌套过深可能影响可读性和性能
