# VariableCalculator 类

## 基本信息
- 类名和包路径: top.maplex.arim.tools.variablecalculator.VariableCalculator
- 基本用途: 表达式解析器，用于解析和计算包含变量的数学表达式
- 类型: 类（Class）
- 所属模块: 变量计算器模块

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> 无

### 类方法
> calculate(expression: String): Double -> 解析并计算不含变量的表达式
> parseContext(expression: String): NodeContext -> 解析表达式并返回上下文对象
> parse(expression: String): Node -> 将字符串表达式解析为节点树
> operator(a1: Node, a2: Node, op: Char): Node -> [私有] 根据操作符创建对应的操作节点
> getPriority(op: Char): Int -> [私有] 获取操作符的优先级

## 实现细节
- 使用"调度场算法"(Shunting-yard algorithm)解析数学表达式
- 通过两个栈（运算符栈和节点栈）实现表达式的解析
- 支持基本运算符：+、-、*、/、%（加、减、乘、除、取模）
- 支持括号()来控制运算优先级
- 支持变量引用，变量名可以是任意非运算符的字符序列
- 支持负数表示（例如-5）
- 支持小数点表示法（例如3.14）

## 使用场景
> 计算带有变量的数学表达式
> 动态解析和计算用户输入的公式
> 实现脚本引擎中的数学运算部分

## 注意事项
> parse方法可能会抛出IllegalStateException异常，调用者需要处理非法操作符的情况
> 表达式中的变量没有显式声明，而是在evaluate阶段通过Map提供值
> 表达式解析功能支持的数学运算有限，不包括函数调用、幂运算等高级功能
