# EffectBezier

## 基本信息
- 类名和包路径: taboolib.module.effect.EffectBezier (Kotlin文件)
- 基本用途: 提供创建各种贝塞尔曲线的便捷方法
- 类型: 工具类（扩展函数集合）
- 所属模块: taboolib.module.effect

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> createTwoRankBezierCurve(p0: Location, p1: Location, p2: Location, step: Double = 1.0, period: Long = 20, spawner: (p: Location) -> Unit = {}): TwoRankBezierCurve -> 创建二阶贝塞尔曲线的快捷方法
> createThreeRankBezierCurve(p0: Location, p1: Location, p2: Location, p3: Location, step: Double = 1.0, period: Long = 20, spawner: (p: Location) -> Unit = {}): ThreeRankBezierCurve -> 创建三阶贝塞尔曲线的快捷方法
> createNRankBezierCurve(points: List<Location>, step: Double = 1.0, period: Long = 20, spawner: (p: Location) -> Unit = {}): NRankBezierCurve -> 使用点列表创建N阶贝塞尔曲线的快捷方法
> createNRankBezierCurve(vararg points: Location, step: Double = 1.0, period: Long = 20, spawner: (p: Location) -> Unit = {}): NRankBezierCurve -> 使用可变参数创建N阶贝塞尔曲线的快捷方法

### 类内可被访问字段
> 无类内可被访问字段（仅扩展函数集合）

### 类方法
> 无类方法（仅顶层函数）

## 实现细节
- 这是一个Kotlin文件，包含了创建各种贝塞尔曲线的扩展函数
- 提供了针对不同阶数贝塞尔曲线的便捷创建方法
- 每个方法都接受必要的位置参数、可选的步长和周期参数，以及一个处理粒子生成的函数
- 使用Kotlin的默认参数和函数字面量简化了贝塞尔曲线的创建过程
- 内部实现通过匿名对象实现ParticleSpawner接口，将用户提供的lambda转换为粒子生成器
- 所有方法都使用建造者模式，支持链式调用
- 支持三种类型的贝塞尔曲线：二阶、三阶和N阶

## 使用场景
> 简化贝塞尔曲线特效的创建过程
> 在Kotlin代码中快速生成各种复杂曲线
> 使用lambda表达式自定义粒子生成逻辑
> 无需直接实现ParticleSpawner接口
> 利用默认参数快速创建标准曲线
> 在需要多阶贝塞尔曲线的复杂特效系统中使用

## 注意事项
> 这些方法专为Kotlin代码设计，虽然可以从Java调用，但会较为繁琐
> 默认步长为1.0，在实际使用中通常需要指定更小的值以获得平滑效果
> 默认周期为20tick（约1秒），可根据需要调整
> spawner参数允许使用lambda表达式自定义粒子生成逻辑
> 如果未提供spawner参数，默认不会生成任何粒子
> N阶贝塞尔曲线提供了两个重载版本，可以使用List或可变参数传入控制点
