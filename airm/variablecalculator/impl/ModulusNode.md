# ModulusNode 类

## 基本信息
- 类名和包路径: top.maplex.arim.tools.variablecalculator.impl.ModulusNode
- 基本用途: 表示取模运算节点，用于处理表达式中的取模操作（求余数）
- 类型: 数据类（Data Class）
- 所属模块: 变量计算器（VariableCalculator）的实现模块

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> left: Node -> 取模操作的被除数节点
> right: Node -> 取模操作的除数节点

### 类方法
> evaluate(variableMap: Map<String, Double>): Double -> 实现Node接口的方法，计算取模操作的结果

## 实现细节
- ModulusNode作为数据类实现，提供了默认的equals()、hashCode()和toString()方法
- evaluate方法首先计算右子节点（除数）的值，并检查是否为零
- 如果除数为零，抛出ArithmeticException异常
- 如果除数非零，计算左子节点的值并返回它们的模运算结果（余数）

## 使用场景
> 表示表达式中的取模操作，如"a % b"
> 在需要计算余数的表达式中使用，例如周期性计算、索引循环等

## 注意事项
> 当除数为零时，会抛出ArithmeticException异常，调用者需要妥善处理
> 在Kotlin中，对于负数的取模操作，结果的符号与除数相同，这与一些其他语言可能有所不同
