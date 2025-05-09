# NodeContext 类

## 基本信息
- 类名和包路径: top.maplex.arim.tools.variablecalculator.NodeContext
- 基本用途: 封装Node节点并提供便捷的求值方法
- 类型: 类（Class）
- 所属模块: 变量计算器（VariableCalculator）

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> node: Node -> 存储计算节点实例

### 类方法
> evaluate(variable: Map<String, Double>): Double -> 使用变量映射表计算节点的值
> evaluate(vararg variables: Pair<String, Double>): Double -> 使用可变参数形式的变量键值对计算节点的值

## 实现细节
- NodeContext是Node的包装类，提供了更便捷的使用方式
- 支持使用可变参数形式传入变量键值对，内部会转换为Map
- node字段是可变的(var)，允许在创建上下文后更改其计算节点

## 使用场景
> 在需要多次计算同一表达式但使用不同变量值的场景
> 作为VariableCalculator.parseContext方法的返回值，用于后续的表达式求值

## 注意事项
> node字段是公开可变的，修改时需注意可能造成的副作用
> 当使用vararg形式的evaluate方法时，如果有重复的变量名，后面的值会覆盖前面的值
