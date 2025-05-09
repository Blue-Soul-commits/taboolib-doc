# ValueNode 类

## 基本信息
- 类名和包路径: top.maplex.arim.tools.variablecalculator.impl.ValueNode
- 基本用途: 表示常量值节点，用于在表达式中表示固定的数值
- 类型: 数据类（Data Class）
- 所属模块: 变量计算器（VariableCalculator）的实现模块

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> value: Double -> 存储常量数值

### 类方法
> evaluate(variableMap: Map<String, Double>): Double -> 实现Node接口的方法，返回存储的常量值

## 实现细节
- ValueNode作为数据类实现，提供了默认的equals()、hashCode()和toString()方法
- evaluate方法直接返回构造时传入的常量值，不受variableMap参数影响
- 作为表达式树中的叶子节点，不需要进一步计算

## 使用场景
> 表示表达式中的数字常量，如"1.5 + x"中的1.5
> 在复杂表达式解析树中作为叶子节点使用

## 注意事项
> 作为数据类，ValueNode是不可变的（immutable），value一旦设置就不能更改
> 由于直接存储Double值，需注意浮点数精度问题
