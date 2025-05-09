# DivisionNode 类

## 基本信息
- 类名和包路径: top.maplex.arim.tools.variablecalculator.impl.DivisionNode
- 基本用途: 表示除法运算节点，用于处理表达式中的除法操作
- 类型: 数据类（Data Class）
- 所属模块: 变量计算器（VariableCalculator）的实现模块

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> left: Node -> 除法操作的被除数节点
> right: Node -> 除法操作的除数节点

### 类方法
> evaluate(variableMap: Map<String, Double>): Double -> 实现Node接口的方法，计算除法操作的结果

## 实现细节
- DivisionNode作为数据类实现，提供了默认的equals()、hashCode()和toString()方法
- evaluate方法首先计算右子节点（除数）的值，并检查是否为零
- 如果除数为零，抛出ArithmeticException异常
- 如果除数非零，计算左子节点的值并返回它们的商

## 使用场景
> 表示表达式中的除法操作，如"a / b"
> 在复杂表达式解析树中作为内部节点使用
