# SubtractionNode 类

## 基本信息
- 类名和包路径: top.maplex.arim.tools.variablecalculator.impl.SubtractionNode
- 基本用途: 表示减法运算节点，用于处理表达式中的减法操作
- 类型: 数据类（Data Class）
- 所属模块: 变量计算器（VariableCalculator）的实现模块

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> left: Node -> 减法操作的左操作数节点
> right: Node -> 减法操作的右操作数节点

### 类方法
> evaluate(variableMap: Map<String, Double>): Double -> 实现Node接口的方法，计算减法操作的结果

## 实现细节
- SubtractionNode作为数据类实现，提供了默认的equals()、hashCode()和toString()方法
- 在evaluate方法中，先计算左右两个子节点的值，然后返回左操作数减去右操作数的差
- 遵循组合模式（Composite Pattern），可以与其他Node实现类组合构建复杂表达式

## 使用场景
> 表示表达式中的减法操作，如"a - b"
> 在复杂表达式解析树中作为内部节点使用

## 注意事项
> 减法操作是非交换的，左右操作数顺序很重要
> 由于是数据类，当对其进行修改时，应当注意其不可变性（immutability）影响
