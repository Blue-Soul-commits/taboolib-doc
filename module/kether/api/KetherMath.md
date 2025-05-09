# KetherMath

## 基本信息
- 类名和包路径: taboolib.module.kether.KetherMath (文件名，非类名)
- 基本用途: 提供Kether脚本中数学运算相关的工具函数，包括类型检查和特殊运算扩展
- 类型: 扩展函数集合
- 所属模块: kether

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> isAllInt(): Boolean -> List<Any>的扩展函数，检查列表中所有元素是否都是整数
> isInt(): Boolean -> Any的扩展函数，检查对象是否可以解析为整数
> subBy(selector: (T) -> Int): Int -> Iterable<T>的扩展函数，对元素应用选择器函数并计算差值
> subByDouble(selector: (T) -> Double): Double -> Iterable<T>的扩展函数，对元素应用选择器函数并计算浮点差值
> mulBy(selector: (T) -> Int): Int -> Iterable<T>的扩展函数，对元素应用选择器函数并计算乘积
> mulByDouble(selector: (T) -> Double): Double -> Iterable<T>的扩展函数，对元素应用选择器函数并计算浮点乘积
> divBy(selector: (T) -> Int): Int -> Iterable<T>的扩展函数，对元素应用选择器函数并计算整数除法结果
> divByDouble(selector: (T) -> Double): Double -> Iterable<T>的扩展函数，对元素应用选择器函数并计算浮点除法结果

### 类内可被访问字段
> 无

### 类方法
> 无（文件中只包含扩展函数）

## 实现细节
- KetherMath提供了一系列扩展函数，用于在Kether脚本中进行数学运算
- isInt()函数通过尝试解析字符串为整数来检查对象是否可以表示为整数
- isAllInt()函数检查列表中的所有元素是否都是整数或可以表示为整数
- subBy和subByDouble实现了减法运算，第一个元素作为起始值，减去后续所有元素
- mulBy和mulByDouble实现了乘法运算，从1开始乘以所有元素
- divBy和divByDouble实现了除法运算，第一个元素作为起始值，除以后续所有元素
- 所有运算函数都接受一个选择器函数，用于从元素中提取数值
- 对空集合的处理：减法和除法返回0（或0.0），乘法返回1（或1.0）

## 使用场景
> 在Kether脚本中进行数学运算，特别是处理列表或集合的运算
> 检查动态值是否可以表示为整数，用于类型验证
> 实现减法、乘法、除法等链式运算，特别是第一个元素与其他元素的关系
> 支持Kether脚本中的数学运算动作实现

## 注意事项
> subBy和divBy函数对第一个元素进行特殊处理，将其作为起始值
> mulBy从1开始乘以所有元素，与subBy和divBy的处理逻辑不同
> isInt()函数依赖于异常捕获，可能对性能有轻微影响
> 除法运算没有处理除数为0的情况，可能导致异常
> 所有函数都使用了inline关键字，以提高性能
