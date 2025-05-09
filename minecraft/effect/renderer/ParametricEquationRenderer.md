# ParametricEquationRenderer

## 基本信息
- 类名和包路径: taboolib.module.effect.renderer.ParametricEquationRenderer
- 基本用途: 用于渲染参数方程曲线的粒子特效，通过函数组x(t)、y(t)、z(t)计算空间中的点位置
- 类型: 粒子特效渲染器
- 所属模块: taboolib.module.effect

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> xFunction: Function<Double, Double> -> 计算x坐标的函数
> yFunction: Function<Double, Double> -> 计算y坐标的函数
> zFunction: Function<Double, Double> -> 计算z坐标的函数
> minT: double -> 参数t的最小值
> maxT: double -> 参数t的最大值
> dt: double -> 参数t的步进值
> currentT: double -> 当前渲染到的t值，用于连续播放特效

### 类方法
> ParametricEquationRenderer(Location origin, Function<Double, Double> xFunction, Function<Double, Double> yFunction, ParticleSpawner spawner): ParametricEquationRenderer -> 创建参数方程渲染器，z函数默认为0
> ParametricEquationRenderer(Location origin, Function<Double, Double> xFunction, Function<Double, Double> yFunction, Function<Double, Double> zFunction, ParticleSpawner spawner): ParametricEquationRenderer -> 创建三维参数方程渲染器，t范围默认为0到360
> ParametricEquationRenderer(Location origin, Function<Double, Double> xFunction, Function<Double, Double> yFunction, Function<Double, Double> zFunction, double minT, double maxT, ParticleSpawner spawner): ParametricEquationRenderer -> 创建自定义t范围的参数方程渲染器
> ParametricEquationRenderer(Location origin, Function<Double, Double> xFunction, Function<Double, Double> yFunction, Function<Double, Double> zFunction, double minT, double maxT, double dT, ParticleSpawner spawner): ParametricEquationRenderer -> 创建完全自定义参数的方程渲染器
> calculateLocations(): List<Location> -> 计算所有粒子应该生成的位置
> show(): void -> 一次性显示所有粒子
> play(): void -> 以周期性方式播放特效，根据步进值逐渐显示粒子
> playNextPoint(): void -> 显示下一个位置的粒子，由播放系统调用
> getMinT(): double -> 获取t的最小值
> setMinT(double minT): ParametricEquationRenderer -> 设置t的最小值并返回自身以支持链式调用
> getMaxT(): double -> 获取t的最大值
> setMaxT(double maxT): ParametricEquationRenderer -> 设置t的最大值并返回自身以支持链式调用
> getDt(): double -> 获取t的步进值
> setDt(double dt): ParametricEquationRenderer -> 设置t的步进值并返回自身以支持链式调用

## 实现细节
- 继承自抽象类ParticleObj，实现了Playable接口
- 使用三个Function<Double, Double>函数对象分别计算任意t值对应的x、y、z值
- 渲染时遍历从minT到maxT的所有参数值，以dt为步长
- 支持三种渲染模式：一次性显示、连续播放、单步播放
- 可以通过矩阵变换来调整粒子的位置和形状
- 每次渲染时，通过ParticleSpawner接口生成实际的粒子效果
- 比普通方程渲染器更强大，可以实现更复杂的曲线和三维效果

## 使用场景
> 创建复杂曲线的粒子特效，如圆、椭圆、螺旋线等
> 生成三维空间中的曲线效果
> 以可视化方式展示参数方程
> 创建动态变化的粒子轨迹和特效
> 实现更为精确的粒子特效路径控制

## 注意事项
> 当minT和maxT范围过大，或dt值过小时，会生成大量粒子，可能影响服务器性能
> 三个函数需要保持数学上的一致性，避免生成无意义的粒子路径
> 播放模式下currentT会持续增加，播放完成后需要手动重置
> 默认参数范围是0到360，适合角度参数，其他类型参数可能需要自定义范围
