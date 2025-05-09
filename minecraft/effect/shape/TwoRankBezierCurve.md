# TwoRankBezierCurve

## 基本信息
- 类名和包路径: taboolib.module.effect.shape.TwoRankBezierCurve
- 基本用途: 用于创建和渲染二阶贝塞尔曲线粒子特效
- 类型: 粒子特效形状类
- 所属模块: taboolib.module.effect.shape

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> locations: List<Location> -> 缓存曲线上所有计算得到的点位
> p0: Location -> 起点
> p1: Location -> 控制点
> p2: Location -> 终点
> step: double -> 参数t的步进值，控制曲线的精度
> currentSample: int -> 当前渲染到的点索引，用于连续播放特效

### 类方法
> TwoRankBezierCurve(Location p0, Location p1, Location p2, ParticleSpawner spawner): TwoRankBezierCurve -> 创建默认步长(0.05)的二阶贝塞尔曲线
> TwoRankBezierCurve(Location p0, Location p1, Location p2, double step, ParticleSpawner spawner): TwoRankBezierCurve -> 创建指定步长的二阶贝塞尔曲线
> calculateLocations(): List<Location> -> 计算贝塞尔曲线上所有粒子位置
> show(): void -> 一次性显示整条贝塞尔曲线的所有粒子
> play(): void -> 以周期性方式播放贝塞尔曲线特效，从起点开始逐渐显示
> playNextPoint(): void -> 显示曲线上的下一个位置的粒子，由播放系统调用
> getP0(): Location -> 获取起点
> setP0(Location p0): TwoRankBezierCurve -> 设置起点并返回自身以支持链式调用
> getP1(): Location -> 获取控制点
> setP1(Location p1): TwoRankBezierCurve -> 设置控制点并返回自身以支持链式调用
> getP2(): Location -> 获取终点
> setP2(Location p2): TwoRankBezierCurve -> 设置终点并返回自身以支持链式调用
> getStep(): double -> 获取步长
> setStep(double step): TwoRankBezierCurve -> 设置步长并返回自身以支持链式调用
> resetLocations(): void -> 重新计算并缓存曲线上的所有点位

## 实现细节
- 继承自抽象类ParticleObj，实现了Playable接口
- 使用二阶贝塞尔曲线算法实现平滑曲线的生成
- 二阶贝塞尔曲线由三个点定义：起点(p0)、控制点(p1)和终点(p2)
- 算法通过递归插值计算曲线上的点：
  1. 计算两组线性插值点：t1(p0→p1), t2(p1→p2)
  2. 最终点为t1→t2的线性插值
- 参数t的范围是[0,1)，控制曲线的生成进度
- 在构造时预计算并缓存所有点位，提高渲染效率
- 支持三种渲染模式：一次性显示、连续播放、单步播放
- 可以通过矩阵变换来调整曲线的位置和形状
- 修改任何控制点或步长参数后会自动重新计算曲线

## 使用场景
> 创建平滑曲线的粒子特效和装饰
> 实现简单弧线动画和过渡效果
> 生成自然弯曲的粒子轨迹
> 连接两点形成平滑曲线
> 用于导航路径的可视化展示
> 模拟简单的抛物线或投掷轨迹

## 注意事项
> 二阶贝塞尔曲线比三阶贝塞尔曲线更简单，只需要一个控制点
> 控制点的位置决定了曲线的形状和弯曲程度
> 步长(step)越小，曲线越平滑，但会生成更多粒子
> 播放模式下currentSample会持续增加，到达末尾后会重置为0
> 修改控制点后需调用resetLocations()方法重新计算曲线，但set系列方法会自动调用
> 在类注释中，作者自嘲算法"很蠢"，但实际上这是标准的二阶贝塞尔曲线算法
