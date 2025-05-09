# Pyramid

## 基本信息
- 类名和包路径: taboolib.module.effect.shape.Pyramid
- 基本用途: 用于创建和渲染N棱锥粒子特效
- 类型: 粒子特效形状类
- 所属模块: taboolib.module.effect.shape

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> locations: List<Location> -> 缓存底面正多边形各顶点的位置
> side: int -> 棱锥底面多边形的边数，必须大于2
> height: double -> 棱锥的高度，从底面中心到顶点的距离
> step: double -> 每个粒子之间的间隔（步长）
> radius: double -> 底面正多边形的半径
> upLoc: Location -> 棱锥顶点的位置

### 类方法
> Pyramid(Location origin, int side, ParticleSpawner spawner): Pyramid -> 创建指定边数、默认半径和高度为1的棱锥
> Pyramid(Location origin, int side, double radius, double height, ParticleSpawner spawner): Pyramid -> 创建指定边数、半径和高度，默认步长为0.02的棱锥
> Pyramid(Location origin, int side, double radius, double height, double step, ParticleSpawner spawner): Pyramid -> 创建完全自定义参数的棱锥
> getSide(): int -> 获取底面多边形的边数
> setSide(int side): Pyramid -> 设置底面多边形的边数并返回自身以支持链式调用
> getHeight(): double -> 获取棱锥的高度
> setHeight(double height): Pyramid -> 设置棱锥的高度并返回自身以支持链式调用
> getStep(): double -> 获取步长
> setStep(double step): Pyramid -> 设置步长并返回自身以支持链式调用
> getRadius(): double -> 获取底面多边形的半径
> setRadius(double radius): Pyramid -> 设置底面多边形的半径并返回自身以支持链式调用
> setOrigin(Location origin): void -> 重写父类方法，设置原点时同时更新顶点位置
> calculateLocations(): List<Location> -> 计算棱锥上所有粒子位置
> show(): void -> 一次性显示整个棱锥的所有粒子
> resetLocations(): void -> 重新计算并缓存底面多边形顶点位置
> buildLine(Location locA, Location locB, double step): void -> [私有] 在两点之间构建直线

## 实现细节
- 继承自抽象类ParticleObj，但未实现Playable接口，只支持静态显示
- 底面是一个正多边形，通过数学方法计算顶点：x = radius * cos(θ), z = radius * sin(θ)
- 顶点位于原点正上方height距离处
- 棱锥由底面的边和从顶点到各底面顶点的棱组成
- 在每条边和棱上均匀分布粒子，间隔由step参数控制
- 底面默认在xOz平面上，顶点沿y轴正方向
- 可以通过矩阵变换来调整棱锥的位置和形状
- 边数必须大于2，否则在构造时会抛出IllegalArgumentException异常
- 修改任何几何参数后会自动重新计算底面顶点位置

## 使用场景
> 创建棱锥形粒子特效和装饰
> 用于魔法、召唤等游戏元素的视觉效果
> 作为特殊标记或符号的可视化表示
> 标记区域范围或技能影响区域
> 实现魔法阵、传送门等游戏元素
> 作为复杂粒子效果系统的组成部分

## 注意事项
> 边数(side)必须大于2，否则会抛出异常
> 不支持动态播放(play)功能，因为未实现Playable接口
> 当边数过多、半径过大或步长过小时，会生成大量粒子，可能影响服务器性能
> 棱锥的位置由原点(origin)决定，原点是底面中心
> 修改原点时会自动更新顶点位置和底面顶点
> 修改任何几何参数后会自动调用resetLocations方法重新计算底面顶点
