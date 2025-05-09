# ConditionEvaluator

## 基本信息
- 类名和包路径: top.maplex.arim.tools.conditionevaluator.ConditionEvaluator
- 基本用途: 条件表达式求值器，用于解析并求值条件表达式
- 类型: 工具类
- 所属模块: Arim条件求值工具模块

## 类结构
### 公开静态字段
> precedence: Map<String, Int> -> 运算符优先级映射表

### 公开方法
> evaluate(expression: String, variable: Map<String, Any>): Boolean -> 使用变量映射求值表达式
> evaluate(expression: String, vararg variable: Pair<String, Any>): Boolean -> 使用可变参数求值表达式
> evaluate(expression: String): Boolean -> 直接求值表达式

### 类内可访问字段
> Value: sealed class -> 值类型密封类
> NumberValue: data class -> 数值类型
> StringValue: data class -> 字符串类型

## 实现细节
- 使用调度场算法(Shunting Yard Algorithm)解析表达式
- 支持数字和字符串类型的比较
- 支持逻辑运算符 && 和 ||
- 支持比较运算符 >, <, >=, <=, ==, !=
- 支持括号分组
- 支持变量替换

## 使用场景
> 需要解析和求值条件表达式时
> 需要动态判断条件时
> 需要支持变量替换的条件判断时

## 注意事项
> 表达式中的值必须用空格分隔
> 字符串值必须用单引号或双引号包围
> 不支持混合类型比较
> 变量替换时会将值转换为字符串