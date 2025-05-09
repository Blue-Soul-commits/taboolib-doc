# DynamicNode 类

## 基本信息
- 类名和包路径: top.maplex.arim.tools.variablecalculator.impl.DynamicNode
- 基本用途: 表示变量节点，用于在表达式中引用动态变量值
- 类型: 数据类（Data Class）
- 所属模块: 变量计算器（VariableCalculator）的实现模块

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> variable: String? = null -> 变量名称，可以为空

### 类方法
> evaluate(variableMap: Map<String, Double>): Double -> 实现Node接口的方法，获取变量的值

## 实现细节
- DynamicNode作为数据类实现，提供了默认的equals()、hashCode()和toString()方法
- variable字段可以为null，构造函数提供了默认值为null
- evaluate方法通过变量名在variableMap中查找对应的值
- 如果变量不存在于映射表中，则返回默认值0.0

## 使用场景
> 在表达式中表示变量，如"a + b"中的a和b
> 用于构建支持变量的动态表达式

## 注意事项
> 当variable为null或变量不存在于variableMap中时，返回默认值0.0
> 在业务需求中，可能需要考虑变量不存在时的其他处理策略
