# ParticleObj

## 基本信息
- 类名和包路径: taboolib.module.effect.ParticleObj
- 基本用途: 表示一个粒子特效对象，提供粒子特效的基础功能和管理
- 类型: 抽象类
- 所属模块: taboolib.module.effect

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> spawner: ParticleSpawner -> 粒子生成器，用于生成实际的粒子效果
> origin: Location -> 特效对象的原点位置
> period: Long -> 特效重复显示的周期，单位为tick
> showType: ShowType -> 特效的显示类型
> running: Boolean -> 特效是否正在运行
> matrix: Matrix? -> 变换矩阵，用于对粒子位置进行变换
> task: PlatformTask? -> 特效运行的任务
> incrementX: Double -> X轴的增量值
> incrementY: Double -> Y轴的增量值
> incrementZ: Double -> Z轴的增量值

### 类方法
> getIncrementX(): Double -> 获取X轴增量
> getIncrementY(): Double -> 获取Y轴增量
> getIncrementZ(): Double -> 获取Z轴增量
> setIncrementX(incrementX: Double): ParticleObj -> 设置X轴增量
> setIncrementY(incrementY: Double): ParticleObj -> 设置Y轴增量
> setIncrementZ(incrementZ: Double): ParticleObj -> 设置Z轴增量
> getMatrix(): Matrix? -> 获取变换矩阵
> addMatrix(matrix: Matrix): ParticleObj -> 为特效对象添加矩阵
> setMatrix(matrix: Matrix?): ParticleObj -> 设置特效对象的矩阵
> removeMatrix(): ParticleObj -> 移除特效对象的矩阵
> hasMatrix(): Boolean -> 检查是否存在矩阵
> show(): Unit -> 抽象方法，显示特效
> calculateLocations(): List<Location> -> 抽象方法，计算特效的位置列表
> alwaysShow(): Unit -> 让特效持续显示（同步）
> alwaysShowAsync(): Unit -> 让特效持续显示（异步）
> alwaysPlay(): Unit -> 让特效持续播放（同步，仅适用于实现了Playable接口的特效）
> alwaysPlayAsync(): Unit -> 让特效持续播放（异步，仅适用于实现了Playable接口的特效）
> turnOffTask(): Unit -> 关闭特效的运行任务
> spawnParticle(location: Location): Unit -> 在指定位置生成粒子，应用矩阵变换和增量

## 实现细节
- 每个特效对象都需要一个ParticleSpawner来实际生成粒子
- 特效可以通过变换矩阵(Matrix)来实现旋转、缩放等效果
- 支持增量设置，可以让特效在原有位置的基础上偏移一定距离
- 提供了同步和异步两种方式的持续显示和播放
- calculateLocations抽象方法需要子类实现，用于计算特效的所有粒子位置
- show抽象方法需要子类实现，用于显示特效
- 提供了链式调用方法，如setIncrementX返回this

## 使用场景
> 创建复杂的粒子特效系统
> 实现持续显示的动态粒子效果
> 对粒子效果应用几何变换
> 创建可交互或动画化的视觉效果

## 注意事项
> alwaysPlay和alwaysPlayAsync方法只能用于实现了Playable接口的特效对象
> 启动新的特效任务前会自动关闭旧的任务
> 矩阵变换是相对于origin原点进行的
> 使用异步方法可能会提高性能，但要注意线程安全问题
> ShowType.NONE表示特效没有自动显示，需要手动调用show方法
