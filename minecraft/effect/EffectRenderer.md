# EffectRenderer

## 基本信息
- 类名和包路径: taboolib.module.effect.EffectRenderer (Kotlin文件)
- 基本用途: 提供创建各种方程渲染器的便捷方法
- 类型: 工具类（扩展函数集合）
- 所属模块: taboolib.module.effect

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> createGeneralEquationRenderer(origin: Location, function: (x: Double) -> Double, minX: Double = -5.0, maxX: Double = 5.0, dx: Double = 0.1, period: Long = 20, spawner: (p: Location) -> Unit = {}): GeneralEquationRenderer -> 创建普通方程渲染器的快捷方法
> createParametricEquationRenderer(origin: Location, xFunction: (x: Double) -> Double, yFunction: (y: Double) -> Double, zFunction: (z: Double) -> Double = { 0.0 }, minT: Double = -5.0, maxT: Double = 5.0, dt: Double = 0.1, period: Long = 20, spawner: (p: Location) -> Unit = {}): ParametricEquationRenderer -> 创建参数方程渲染器的快捷方法
> createPolarEquationRenderer(origin: Location, rFunction: (r: Double) -> Double, minT: Double = -5.0, maxT: Double = 5.0, dt: Double = 0.1, period: Long = 20, spawner: (p: Location) -> Unit = {}): PolarEquationRenderer -> 创建极坐标方程渲染器的快捷方法

### 类内可被访问字段
> 无类内可被访问字段（仅扩展函数集合）

### 类方法
> 无类方法（仅顶层函数）

## 实现细节
- 这是一个Kotlin文件，包含了创建各种数学方程渲染器的扩展函数
- 提供了三种主要类型的方程渲染器的快捷创建方法：普通方程、参数方程和极坐标方程
- 每个方法都接受必要的位置参数、函数参数、方程范围参数、可选的周期参数，以及一个处理粒子生成的函数
- 使用Kotlin的默认参数和函数字面量简化了方程渲染器的创建过程
- 内部实现通过匿名对象实现ParticleSpawner接口，将用户提供的lambda转换为粒子生成器
- 所有方法都使用建造者模式，支持链式调用
- 为常用参数提供了合理的默认值，如方程范围和步长

## 使用场景
> 创建基于数学方程的复杂粒子特效
> 可视化数学函数和曲线
> 生成函数图像、参数曲线和极坐标曲线
> 实现各种特殊曲线如抛物线、正弦曲线、螺旋线等
> 创建基于数学公式的动态粒子动画
> 在教育或展示中可视化数学概念

## 注意事项
> 这些方法专为Kotlin代码设计，虽然可以从Java调用，但会较为繁琐
> 默认的方程范围一般为-5.0到5.0，步长为0.1，可根据需要调整
> 参数方程的z函数默认返回0，使曲线默认在xOy平面上
> 极坐标方程使用角度作为参数，生成平面曲线
> spawner参数允许使用lambda表达式自定义粒子生成逻辑
> 如果未提供spawner参数，默认不会生成任何粒子
> 函数参数使用Kotlin的函数类型，可以直接使用lambda表达式定义数学函数
