# Ray

## 基本信息
- 类名和包路径: taboolib.module.effect.shape.Ray
- 基本用途: 用于创建和渲染射线/光束粒子特效
- 类型: 粒子特效形状类
- 所属模块: taboolib.module.effect.shape

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> direction: Vector -> 射线的方向向量
> maxLength: double -> 射线的最大长度
> step: double -> 每个粒子之间的间隔（步长）
> range: double -> 射线的检测范围（用于碰撞检测）
> stopType: RayStopType -> 射线停止类型，决定射线何时终止
> currentStep: double -> 当前渲染到的位置，用于连续播放特效

### 类方法
> Ray(Location origin, Vector direction, double maxLength, ParticleSpawner spawner): Ray -> 创建指定方向和最大长度，默认步长0.2的射线
> Ray(Location origin, Vector direction, double maxLength, double step, ParticleSpawner spawner): Ray -> 创建指定方向、最大长度和步长，默认检测范围0.5的射线
> Ray(Location origin, Vector direction, double maxLength, double step, double range, RayStopType stopType, long period, ParticleSpawner spawner): Ray -> 创建完全自定义参数的射线
> show(): void -> 一次性显示整条射线的所有粒子
> calculateLocations(): List<Location> -> 计算射线上所有粒子位置
> play(): void -> 以周期性方式播放射线特效，从起点开始逐渐延伸
> playNextPoint(): void -> 显示射线上的下一个位置的粒子，由播放系统调用
> getDirection(): Vector -> 获取射线方向向量
> setDirection(Vector direction): Ray -> 设置射线方向向量并返回自身以支持链式调用
> getMaxLength(): double -> 获取射线最大长度
> setMaxLength(double maxLength): Ray -> 设置射线最大长度并返回自身以支持链式调用
> getStep(): double -> 获取步长
> setStep(double step): Ray -> 设置步长并返回自身以支持链式调用
> getRange(): double -> 获取检测范围
> setRange(double range): Ray -> 设置检测范围并返回自身以支持链式调用
> getStopType(): RayStopType -> 获取停止类型
> setStopType(RayStopType stopType): Ray -> 设置停止类型并返回自身以支持链式调用

## 实现细节
- 继承自抽象类ParticleObj，实现了Playable接口
- 射线沿着指定的方向向量延伸，长度由maxLength控制
- 支持三种渲染模式：一次性显示、连续播放、单步播放
- 默认使用MAX_LENGTH停止类型，即射线延伸到指定长度后停止
- 可以通过矩阵变换来调整射线的位置和形状
- 每次渲染时，通过ParticleSpawner接口生成实际的粒子效果
- 虽然提供了range参数和stopType枚举，但当前实现仅支持MAX_LENGTH一种停止类型

## 使用场景
> 创建光束、激光等直线型粒子特效
> 模拟射击、魔法释放等游戏元素的视觉效果
> 指示方向或路径
> 实现追踪效果或引导系统
> 作为复杂粒子效果系统的基础组件
> 用于技能释放的视觉表现

## 注意事项
> direction向量会影响射线的方向，通常应该是一个单位向量
> 尽管定义了RayStopType枚举和range参数，但当前实现只使用了MAX_LENGTH类型
> 当最大长度过大或步长过小时，会生成大量粒子，可能影响服务器性能
> 播放模式下currentStep会持续增加，超过maxLength后会重置为0
> 射线是直线的，不支持曲线或弯曲效果
> 如需实现碰撞检测等功能，需要额外扩展
