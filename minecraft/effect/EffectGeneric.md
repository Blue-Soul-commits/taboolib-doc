# EffectGeneric

## 基本信息
- 类名和包路径: taboolib.module.effect.EffectGeneric (Kotlin文件)
- 基本用途: 提供创建各种常见粒子特效形状的便捷方法
- 类型: 工具类（扩展函数集合）
- 所属模块: taboolib.module.effect

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> createLotus(origin: Location, period: Long = 20, spawner: (p: Location) -> Unit = {}): Lotus -> 创建莲花特效的快捷方法
> createRay(origin: Location, direction: Vector, maxLength: Double, step: Double, range: Double = 0.5, stopType: RayStopType, period: Long = 20L, spawner: (p: Location) -> Unit = {}): Ray -> 创建射线特效的快捷方法
> createStar(origin: Location, radius: Double, step: Double, period: Long = 20L, spawner: (p: Location) -> Unit = {}): Star -> 创建五角星特效的快捷方法
> createHeart(xScaleRate: Double, yScaleRate: Double, origin: Location, period: Long, spawner: (p: Location) -> Unit = {}): Heart -> 创建心形特效的快捷方法
> createArc(origin: Location, startAngle: Double = 0.0, angle: Double = 30.0, radius: Double = 1.0, step: Double = 1.0, period: Long = 20, spawner: (p: Location) -> Unit = {}): Arc -> 创建弧形特效的快捷方法
> createAstroid(origin: Location, radius: Double = 1.0, step: Double = 1.0, period: Long = 20, spawner: (p: Location) -> Unit = {}): Astroid -> 创建星形线特效的快捷方法
> createCircle(origin: Location, radius: Double = 1.0, step: Double = 1.0, period: Long = 20, spawner: (p: Location) -> Unit = {}): Circle -> 创建圆形特效的快捷方法
> createFilledCircle(origin: Location, radius: Double = 1.0, sample: Int = 100, period: Long = 20, spawner: (p: Location) -> Unit = {}): FilledCircle -> 创建实心圆特效的快捷方法
> createCube(min: Location, max: Location, step: Double = 1.0, period: Long = 20, spawner: (p: Location) -> Unit = {}): Cube -> 创建立方体特效的快捷方法
> createLine(start: Location, end: Location, step: Double = 1.0, period: Long = 20, spawner: (p: Location) -> Unit = {}): Line -> 创建直线特效的快捷方法
> createPolygon(origin: Location, radius: Double = 1.0, sides: Int = 3, step: Double = 1.0, period: Long = 20, spawner: (p: Location) -> Unit = {}): Polygon -> 创建正多边形特效的快捷方法
> createSphere(origin: Location, radius: Double = 1.0, sample: Int = 100, period: Long = 20, spawner: (p: Location) -> Unit = {}): Sphere -> 创建球体特效的快捷方法

### 类内可被访问字段
> 无类内可被访问字段（仅扩展函数集合）

### 类方法
> 无类方法（仅顶层函数）

## 实现细节
- 这是一个Kotlin文件，包含了创建各种通用粒子特效形状的扩展函数
- 使用@file:Suppress("SpellCheckingInspection")抑制拼写检查警告
- 提供了对所有主要形状类的快捷创建方法，包括：莲花、射线、星形、心形、弧形、星形线、圆形、实心圆、立方体、直线、多边形和球体
- 每个方法都接受必要的位置参数、可选的形状参数、周期参数，以及一个处理粒子生成的函数
- 使用Kotlin的默认参数和函数字面量简化了特效形状的创建过程
- 内部实现通过匿名对象实现ParticleSpawner接口，将用户提供的lambda转换为粒子生成器
- 所有方法都使用建造者模式，支持链式调用
- 大多数方法都提供了合理的默认参数值，便于快速创建

## 使用场景
> 简化各种粒子特效形状的创建过程
> 在Kotlin代码中快速生成常见的粒子效果
> 使用lambda表达式自定义粒子生成逻辑
> 无需直接实现ParticleSpawner接口
> 利用默认参数快速创建标准形状
> 在需要多种形状组合的复杂特效系统中使用

## 注意事项
> 这些方法专为Kotlin代码设计，虽然可以从Java调用，但会较为繁琐
> 大多数形状都有默认的尺寸参数，但实际使用中通常需要调整以符合具体需求
> 默认周期一般为20tick（约1秒），可根据需要调整
> spawner参数允许使用lambda表达式自定义粒子生成逻辑
> 如果未提供spawner参数，默认不会生成任何粒子
> 注意createLotus方法中的spawner实现有个bug：它传递的是origin而不是location
> 不同形状的创建方法参数组织方式略有不同，使用前应查看文档
