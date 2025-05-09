# Equations

## 基本信息
- 类名和包路径: taboolib.module.effect.math.Equations
- 基本用途: 提供常用数学函数的函数式接口实现
- 类型: 工具类
- 所属模块: taboolib.module.effect.math

## 类结构

### 公开静态字段
> QUADRATIC_FUNCTION: Function<Double, Double> -> 二次函数 f(x) = x²
> LINEAR_FUNCTION: Function<Double, Double> -> 一次函数 f(x) = x
> COS_FUNCTION: Function<Double, Double> -> 余弦函数 f(x) = cos(x)
> SIN_FUNCTION: Function<Double, Double> -> 正弦函数 f(x) = sin(x)
> POLAR_FOUR_LEAVE_CURVE: Function<Double, Double> -> 极坐标四叶玫瑰线 r = 1.5 * sin(2θ)

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> 无类内可被访问字段

### 类方法
> 无实例方法

## 实现细节
- 所有函数都使用Java 8的Function函数式接口实现
- QUADRATIC_FUNCTION使用Math.pow方法实现二次方计算
- LINEAR_FUNCTION直接返回输入参数
- COS_FUNCTION和SIN_FUNCTION分别使用Math.cos和Math.sin方法实现
- POLAR_FOUR_LEAVE_CURVE实现了四叶玫瑰线的极坐标方程

## 使用场景
> 粒子效果中的轨迹生成
> 动画效果的参数计算
> 几何图形的绘制
> 数学模型的构建和计算
> 函数式编程风格的数学计算

## 注意事项
> 所有函数接收Double类型参数并返回Double类型结果
> 使用函数式接口使得这些函数可以方便地用于流处理和函数组合
> 极坐标四叶玫瑰线函数在极坐标系中使用，需要结合极坐标转换使用
