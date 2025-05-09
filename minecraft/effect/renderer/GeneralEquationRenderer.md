# GeneralEquationRenderer

## 基本信息
- 类名和包路径: taboolib.module.effect.renderer.GeneralEquationRenderer
- 基本用途: 用于渲染普通方程曲线的粒子特效，通过函数f(x)计算y坐标，并在对应位置生成粒子
- 类型: 粒子特效渲染器
- 所属模块: taboolib.module.effect

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> function: Function<Double, Double> -> 用于计算y坐标的函数
> minX: double -> x坐标的最小值
> maxX: double -> x坐标的最大值
> dx: double -> x坐标的步进值
> currentX: double -> 当前渲染到的x坐标，用于连续播放特效

### 类方法
> GeneralEquationRenderer(Location origin, Function<Double, Double> function, ParticleSpawner spawner): GeneralEquationRenderer -> 使用默认范围(-5.0到5.0)创建方程渲染器
> GeneralEquationRenderer(Location origin, Function<Double, Double> function, double minX, double maxX, ParticleSpawner spawner): GeneralEquationRenderer -> 使用指定x轴范围和默认步进值(0.1)创建方程渲染器
> GeneralEquationRenderer(Location origin, Function<Double, Double> function, double minX, double maxX, double dx, ParticleSpawner spawner): GeneralEquationRenderer -> 使用完全自定义参数创建方程渲染器
> calculateLocations(): List<Location> -> 计算所有粒子应该生成的位置
> show(): void -> 一次性显示所有粒子
> play(): void -> 以周期性方式播放特效，根据步进值逐渐显示粒子
> playNextPoint(): void -> 显示下一个位置的粒子，由播放系统调用
> getMinX(): double -> 获取x的最小值
> setMinX(double minX): GeneralEquationRenderer -> 设置x的最小值并返回自身以支持链式调用
> getMaxX(): double -> 获取x的最大值
> setMaxX(double maxX): GeneralEquationRenderer -> 设置x的最大值并返回自身以支持链式调用
> getDx(): double -> 获取x的步进值
> setDx(double dx): GeneralEquationRenderer -> 设置x的步进值并返回自身以支持链式调用

## 实现细节
- 继承自抽象类ParticleObj，实现了Playable接口
- 使用Function<Double, Double>函数对象来计算任意x值对应的y值
- 渲染时遍历从minX到maxX的所有点，以dx为步长
- 支持三种渲染模式：一次性显示、连续播放、单步播放
- 可以通过矩阵变换来调整粒子的位置和形状
- 每次渲染时，通过ParticleSpawner接口生成实际的粒子效果

## 使用场景
> 创建函数图像的粒子特效，例如抛物线、正弦曲线等
> 以可视化方式展示数学函数
> 创建具有特定数学特性的装饰性粒子效果
> 作为复杂粒子效果系统的一部分，生成特定曲线形状

## 注意事项
> 当minX和maxX范围过大，或dx值过小时，会生成大量粒子，可能影响服务器性能
> 函数计算结果只影响y坐标，x和z坐标需要通过其他方式（如矩阵变换）调整
> 默认情况下，函数曲线在xOy平面上（z坐标为0）
> 播放模式下currentX会持续增加，播放完成后需要手动重置

