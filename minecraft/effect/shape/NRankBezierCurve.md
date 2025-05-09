# NRankBezierCurve

## 基本信息
- 类名和包路径: taboolib.module.effect.shape.NRankBezierCurve
- 基本用途: 用于创建和渲染N阶贝塞尔曲线的粒子特效
- 类型: 粒子特效形状类
- 所属模块: taboolib.module.effect.shape

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> calculateCurve(List<Location> locList, double t): Location -> [私有] 递归计算贝塞尔曲线上给定参数t对应的点位置

### 类内可被访问字段
> points: List<Location> -> 保存曲线上所有计算得到的点位
> step: double -> 参数t的步进值，控制曲线的精度
> locations: List<Location> -> 用于定义贝塞尔曲线的控制点列表
> currentSample: int -> 当前渲染到的点索引，用于连续播放特效

### 类方法
> NRankBezierCurve(List<Location> locations, ParticleSpawner spawner): NRankBezierCurve -> 创建默认步长(0.05)的N阶贝塞尔曲线
> NRankBezierCurve(List<Location> locations, double step, ParticleSpawner spawner): NRankBezierCurve -> 创建指定步长的N阶贝塞尔曲线
> calculateLocations(): List<Location> -> 计算贝塞尔曲线上所有粒子位置
> show(): void -> 一次性显示整条贝塞尔曲线的所有粒子
> play(): void -> 以周期性方式播放贝塞尔曲线特效，从起点开始逐渐显示
> playNextPoint(): void -> 显示曲线上的下一个位置的粒子，由播放系统调用
> resetLocation(): void -> 重新计算并缓存曲线上的所有点位

## 实现细节
- 继承自抽象类ParticleObj，实现了Playable接口
- 使用递归算法实现任意阶数贝塞尔曲线的计算
- 贝塞尔曲线算法基于德卡斯特里奥(de Casteljau)算法，通过递归降阶生成曲线
- 参数t的范围是[0,1)，控制曲线的生成进度
- 在构造时预计算并缓存所有点位，提高渲染效率
- 支持三种渲染模式：一次性显示、连续播放、单步播放
- 可以通过矩阵变换来调整曲线的位置和形状
- 曲线的平滑度和精度由step步长参数控制

## 使用场景
> 创建平滑曲线的粒子特效和装饰
> 实现复杂路径动画和过渡效果
> 生成自然流畅的粒子轨迹
> 连接多个点位形成平滑曲线
> 用于导航路径的可视化展示
> 模拟物体沿复杂路径的运动

## 注意事项
> 控制点数量决定了贝塞尔曲线的阶数(n = 控制点数量 - 1)
> 控制点数量越多，计算复杂度越高，但曲线形状控制更精确
> 步长(step)越小，曲线越平滑，但会生成更多粒子
> 播放模式下currentSample会持续增加，到达末尾后会重置为0
> 修改控制点后需调用resetLocation()方法重新计算曲线
> 控制点应该在同一个世界中，否则可能会出现异常

