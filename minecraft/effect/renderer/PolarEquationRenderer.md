# PolarEquationRenderer

## 基本信息
- 类名和包路径: taboolib.module.effect.renderer.PolarEquationRenderer
- 基本用途: 用于渲染极坐标方程曲线的粒子特效，通过极坐标函数ρ = f(θ)生成曲线
- 类型: 粒子特效渲染器
- 所属模块: taboolib.module.effect

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> function: Function<Double, Double> -> 极坐标方程函数，输入角度θ，返回半径ρ
> minTheta: double -> 角度θ的最小值
> maxTheta: double -> 角度θ的最大值
> dTheta: double -> 角度θ的步进值
> currentTheta: double -> 当前渲染到的角度值，用于连续播放特效

### 类方法
> PolarEquationRenderer(Location origin, Function<Double, Double> function, ParticleSpawner spawner): PolarEquationRenderer -> 创建极坐标渲染器，默认角度范围为0到360度
> PolarEquationRenderer(Location origin, Function<Double, Double> function, double minTheta, double maxTheta, double dTheta, ParticleSpawner spawner): PolarEquationRenderer -> 创建自定义角度范围的极坐标渲染器
> calculateLocations(): List<Location> -> 计算所有粒子应该生成的位置
> show(): void -> 一次性显示所有粒子
> play(): void -> 以周期性方式播放特效，根据步进值逐渐显示粒子
> playNextPoint(): void -> 显示下一个位置的粒子，由播放系统调用
> getMinTheta(): double -> 获取θ的最小值
> setMinTheta(double minTheta): PolarEquationRenderer -> 设置θ的最小值并返回自身以支持链式调用
> getMaxTheta(): double -> 获取θ的最大值
> setMaxTheta(double maxTheta): PolarEquationRenderer -> 设置θ的最大值并返回自身以支持链式调用
> getDTheta(): double -> 获取θ的步进值
> setDTheta(double dTheta): PolarEquationRenderer -> 设置θ的步进值并返回自身以支持链式调用

## 实现细节
- 继承自抽象类ParticleObj，实现了Playable接口
- 使用Function<Double, Double>函数对象计算角度θ对应的半径ρ
- 通过极坐标与直角坐标转换公式x = ρcos(θ)，y = ρsin(θ)计算粒子位置
- 渲染时遍历从minTheta到maxTheta的所有角度，以dTheta为步长
- 支持三种渲染模式：一次性显示、连续播放、单步播放
- 可以通过矩阵变换来调整粒子的位置和形状
- 每次渲染时，通过ParticleSpawner接口生成实际的粒子效果
- 默认在xOy平面上生成粒子（z坐标为0）

## 使用场景
> 创建基于极坐标的特殊曲线，如心形线、玫瑰线、螺线等
> 生成具有特定极坐标方程特性的粒子效果
> 以可视化方式展示极坐标方程
> 创建旋转对称的粒子图案和特效
> 实现特定的装饰性特效图案

## 注意事项
> 当minTheta和maxTheta范围过大，或dTheta值过小时，会生成大量粒子，可能影响服务器性能
> 函数计算结果应当合理，过大的值可能导致特效超出可见范围
> 默认情况下，极坐标曲线在xOy平面上，要实现三维效果需要使用矩阵变换
> 播放模式下currentTheta会持续增加，播放完成后需要手动重置
> 注意极坐标方程中使用的角度单位，代码中默认使用弧度制进行计算
