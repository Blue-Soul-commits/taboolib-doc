# ParserUtils

## 基本信息
- 类名和包路径: top.maplex.arim.tools.entitymatch.util.ParserUtils
- 基本用途: 实体匹配条件解析工具类，用于解析各种格式的条件表达式
- 类型: 工具类
- 所属模块: Arim实体匹配工具模块

## 类结构
### 公开静态方法
> splitConditions(expression: String): List<String> -> 分割条件表达式
> parseKeyValue(condition: String): Pair<String, String>? -> 解析键值对
> parseStringCondition(value: String): MatchCondition.StringCondition -> 解析字符串条件
> parseListCondition(value: String): MatchCondition -> 解析列表条件
> parseNumberCondition(value: String): MatchCondition.NumberCondition -> 解析数值条件

### 类内可访问字段
> 无

## 实现细节
- 支持多种条件表达式格式解析
- 支持嵌套条件解析
- 支持修饰符处理
- 支持多种操作符和比较方式
- 支持颜色代码处理

## 使用场景
> 需要解析实体匹配条件时
> 需要处理复杂条件表达式时
> 需要转换条件格式时

## 注意事项
> 字符串条件支持多种操作符简写
> 数值条件支持标签前缀
> 列表条件支持复合类型
> 条件表达式需要正确的格式

## 使用实例
> 解析字符串条件
```kotlin
// 解析精确匹配
val exact = ParserUtils.parseStringCondition("exact(\"test\")")

// 解析包含匹配
val contains = ParserUtils.parseStringCondition("contains(\"test\")")

// 解析带修饰符的条件
val withModifier = ParserUtils.parseStringCondition("contains[uncolored](\"test\")")
```

> 解析数值条件
```kotlin
// 解析简单数值
val simple = ParserUtils.parseNumberCondition("10")

// 解析带操作符的数值
val withOperator = ParserUtils.parseNumberCondition(">10")

// 解析带标签的数值
val withTag = ParserUtils.parseNumberCondition("health>10")
```

> 解析列表条件
```kotlin
// 解析复合条件
val compound = ParserUtils.parseListCondition("any(contains(\"test\"),startsWith(\"a\"))")

// 解析嵌套条件
val nested = ParserUtils.parseListCondition("all(any(contains(\"a\"),contains(\"b\")),startsWith(\"c\"))")
```