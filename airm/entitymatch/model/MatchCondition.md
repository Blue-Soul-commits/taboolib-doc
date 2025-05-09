# Conditions

## 基本信息
- 类名和包路径: top.maplex.arim.tools.entitymatch.model.Conditions
- 基本用途: 实体匹配条件模型，用于定义实体匹配的各种条件类型
- 类型: 数据模型类
- 所属模块: Arim实体匹配工具模块

## 类结构
### 公开静态字段
> StringOperation: enum class -> 字符串操作类型枚举
> NumberOperator: enum class -> 数值操作符枚举
> CompoundType: enum class -> 复合条件类型枚举

### 公开方法
> MatchCondition: sealed class -> 匹配条件基类
> StringCondition: data class -> 字符串条件类
> NumberCondition: data class -> 数值条件类
> CompoundCondition: data class -> 复合条件类

### 类内可访问字段
> modifiers: List<String> -> 条件修饰符列表
> operation: StringOperation -> 字符串操作类型
> values: List<String> -> 字符串值列表
> operator: NumberOperator -> 数值操作符
> value: Double -> 数值
> tag: String -> 数值条件标签
> type: CompoundType -> 复合条件类型
> conditions: List<MatchCondition> -> 子条件列表

## 实现细节
- 使用密封类(sealed class)定义条件类型
- 支持字符串匹配、数值比较和复合条件
- 所有条件类型都支持修饰符
- 数值条件支持标签标记

## 使用场景
> 需要定义实体匹配条件时
> 需要组合多个匹配条件时
> 需要支持不同类型的条件匹配时

## 注意事项
> 字符串条件支持多种匹配方式
> 数值条件可以添加标签
> 复合条件可以嵌套使用
> 所有条件都支持修饰符