# Line

## 基本信息
- 类名和包路径: taboolib.module.effect.shape.Line
- 基本用途: 用于创建和渲染直线粒子特效
- 类型: 粒子特效形状类
- 所属模块: taboolib.module.effect.shape

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> buildLine(Location locA, Location locB, double step, ParticleSpawner spawner): void -> 静态方法，直接在两点之间构建并显示一条直线

### 类内可被访问字段
> vector: Vector -> 线的方向向量（单位向量）
> start: Location -> 线的起点位置
> end: Location -> 线的终点位置
> step: double -> 每个粒子之间的间隔（步长）
> length: double -> 线的长度
> currentStep: double -> 当前渲染到的位置，用于连续播放特效

### 类方法
> Line(Location start, Location end, ParticleSpawner spawner): Line -> 创建默认步长(0.1)的直线
> Line(Location start, Location end, double step, ParticleSpawner spawner): Line -> 创建指定步长的直线，默认周期为20tick
> Line(Location start, Location end, double step, long period, ParticleSpawner spawner): Line -> 创建完全自定义参数的直线
> calculateLocations(): List<Location> -> 计算直线上所有粒子位置
> show(): void -> 一次性显示整条直线的所有粒子
> play(): void -> 以周期性方式播放直线特效，从起点开始逐渐显示到终点
> playNextPoint(): void -> 显示直线上的下一个位置的粒子，由播放系统调用
> getStart(): Location -> 获取线的起点
> setStart(Location start): Line -> 设置线的起点并返回自身以支持链式调用
> getEnd(): Location -> 获取线的终点
> setEnd(Location end): Line -> 设置线的终点并返回自身以支持链式调用
> getStep(): double -> 获取步长
> setStep(double step): Line -> 设置步长并返回自身以支持链式调用
> resetVector(): void -> 手动重新计算线的向量和长度

## 实现细节
- 继承自抽象类ParticleObj，实现了Playable接口
- 通过起点和终点计算归一化方向向量和总长度
- 渲染时沿着向量方向，以步长为间隔生成粒子
- 支持三种渲染模式：一次性显示、连续播放、单步播放
- 提供静态方法buildLine直接在两点间显示直线，无需创建对象
- 每次渲染时，通过ParticleSpawner接口生成实际的粒子效果
- 当修改起点、终点或步长时，会自动重新计算向量参数

## 使用场景
> 创建直线型粒子特效和装饰
> 用于显示两点之间的连接关系
> 实现射线、光束、轨迹等视觉效果
> 标记路径、方向或移动轨迹
> 作为复杂粒子效果系统的基础组件
> 创建网格、框架等需要直线段的结构

## 注意事项
> 如果起点和终点在不同世界，可能会出现异常
> 当线段过长或步长过小时，会生成大量粒子，可能影响服务器性能
> 修改起点、终点或步长后会自动调用resetVector重新计算向量参数
> 播放模式下currentStep会持续增加，超过线长后会重置为0
> 静态方法buildLine适合一次性显示，不支持动画效果
> 粒子生成是从起点到终点的顺序

