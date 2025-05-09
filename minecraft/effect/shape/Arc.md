# Arc

## 基本信息
- 类名和包路径: taboolib.module.effect.shape.Arc
- 基本用途: 用于创建和渲染弧形粒子特效
- 类型: 粒子特效形状类
- 所属模块: taboolib.module.effect.shape

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> startAngle: double -> 弧的起始角度，默认为0度
> angle: double -> 弧总共的角度范围
> radius: double -> 弧所在圆的半径
> step: double -> 每个粒子的角度间隔(步长)
> currentAngle: double -> 当前渲染到的角度，用于连续播放特效

### 类方法
> Arc(Location origin, ParticleSpawner spawner): Arc -> 创建默认角度为30度的弧
> Arc(Location origin, double angle, ParticleSpawner spawner): Arc -> 创建指定角度、默认半径为1的弧
> Arc(Location origin, double angle, double radius, ParticleSpawner spawner): Arc -> 创建指定角度和半径、默认步长为1的弧
> Arc(Location origin, double angle, double radius, double step, ParticleSpawner spawner): Arc -> 创建指定角度、半径和步长的弧，默认周期为20tick
> Arc(Location origin, double angle, double radius, double step, long period, ParticleSpawner spawner): Arc -> 从零度角开始构造完全自定义的弧
> Arc(Location origin, double startAngle, double angle, double radius, double step, long period, ParticleSpawner spawner): Arc -> 从指定起始角度构造完全自定义的弧
> calculateLocations(): List<Location> -> 计算弧上所有粒子位置
> show(): void -> 一次性显示整个弧的所有粒子
> play(): void -> 以周期性方式播放弧的特效，从起始点开始逐渐显示
> playNextPoint(): void -> 显示弧上的下一个位置的粒子，由播放系统调用
> getStartAngle(): double -> 获取起始角度
> setStartAngle(double startAngle): Arc -> 设置起始角度并返回自身以支持链式调用
> getAngle(): double -> 获取弧的总角度
> setAngle(double angle): Arc -> 设置弧的总角度并返回自身以支持链式调用
> getRadius(): double -> 获取弧的半径
> setRadius(double radius): Arc -> 设置弧的半径并返回自身以支持链式调用
> getStep(): double -> 获取步长
> setStep(double step): Arc -> 设置步长并返回自身以支持链式调用

## 实现细节
- 继承自抽象类ParticleObj，实现了Playable接口
- 通过三角函数计算弧上的点位置：x = radius * cos(角度)，z = radius * sin(角度)
- 弧默认在xOz平面上生成，y坐标默认为0
- 渲染时遍历从startAngle到angle的所有角度，以step为步长
- 支持三种渲染模式：一次性显示、连续播放、单步播放
- 可以通过矩阵变换来调整弧的位置和形状
- 每次渲染时，通过ParticleSpawner接口生成实际的粒子效果
- 注意角度使用度为单位，在计算时需要转换为弧度

## 使用场景
> 创建弧形粒子特效和装饰
> 实现圆形进度条效果
> 设计扇形区域标记或提示
> 用于技能释放范围的可视化展示
> 制作部分圆形或弧形的视觉效果
> 作为复杂粒子效果的组成部分

## 注意事项
> 角度使用的是度数而非弧度，计算时会自动转换
> 默认在xOz平面上生成弧，如需在其他平面生成需使用矩阵变换
> 当角度范围过大、半径过大或步长过小时，会生成大量粒子，可能影响性能
> 播放模式下currentAngle会持续增加，超过最大角度后会重置
> 如果需要闭合的圆，请使用Circle类而非设置角度为360度的Arc
