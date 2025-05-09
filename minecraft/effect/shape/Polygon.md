# Polygon

## 基本信息
- 类名和包路径: taboolib.module.effect.shape.Polygon
- 基本用途: 用于创建和渲染正多边形粒子特效
- 类型: 粒子特效形状类
- 所属模块: taboolib.module.effect.shape

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> locations: List<Location> -> 缓存正多边形各顶点的位置
> side: int -> 多边形的边数，必须大于2
> step: double -> 每个粒子之间的间隔（步长）
> radius: double -> 正多边形的半径

### 类方法
> Polygon(int side, Location origin, ParticleSpawner spawner): Polygon -> 创建指定边数、默认步长(0.02)的正多边形
> Polygon(int side, Location origin, double step, ParticleSpawner spawner): Polygon -> 创建指定边数和步长的正多边形
> getSide(): int -> 获取多边形的边数
> setSide(int side): Polygon -> 设置多边形的边数并返回自身以支持链式调用
> getStep(): double -> 获取步长
> setStep(double step): Polygon -> 设置步长并返回自身以支持链式调用
> getRadius(): double -> 获取半径
> setRadius(double radius): Polygon -> 设置半径并返回自身以支持链式调用
> calculateLocations(): List<Location> -> 计算正多边形上所有粒子位置
> show(): void -> 一次性显示整个正多边形的所有粒子
> resetLocations(): void -> 重新计算并缓存多边形顶点位置
> buildLine(Location locA, Location locB, double step): void -> [私有] 在两点之间构建直线

## 实现细节
- 继承自抽象类ParticleObj，但未实现Playable接口，只支持静态显示
- 通过数学方法计算正多边形的顶点：x = cos(θ) * radius, z = sin(θ) * radius
- 顶点角度均匀分布在圆周上，角度间隔为360/side度
- 边由相邻顶点连接形成，最后一个顶点与第一个顶点相连形成闭环
- 在每条边上均匀分布粒子，间隔由step参数控制
- 默认在xOz平面上生成正多边形，y坐标默认为0
- 可以通过矩阵变换来调整正多边形的位置和形状
- 边数必须大于2，否则在构造时会抛出IllegalArgumentException异常
- 缓存顶点位置以提高渲染效率，修改任何参数后会自动重新计算

## 使用场景
> 创建各种正多边形粒子特效和装饰
> 标记区域范围或技能影响范围
> 作为游戏元素的视觉边界
> 用于生成几何图形特效
> 作为复杂粒子效果系统的基础组件
> 实现多边形魔法阵或仪式效果

## 注意事项
> 边数(side)必须大于2，否则会抛出异常
> 不支持动态播放(play)功能，因为未实现Playable接口
> 当边数过多或步长过小时，会生成大量粒子，可能影响服务器性能
> 默认在xOz平面上生成，如需在其他平面生成需使用矩阵变换
> 修改边数、步长或半径后会自动调用resetLocations方法重新计算顶点
> radius默认为0，使用前需要先设置有效的半径值
