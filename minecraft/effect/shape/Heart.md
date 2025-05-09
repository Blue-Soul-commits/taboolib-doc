# Heart

## 基本信息
- 类名和包路径: taboolib.module.effect.shape.Heart
- 基本用途: 用于创建和渲染心形线粒子特效
- 类型: 粒子特效形状类
- 所属模块: taboolib.module.effect.shape

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> xScaleRate: double -> X轴缩放比率，控制心形水平方向的大小
> yScaleRate: double -> Y轴缩放比率，控制心形垂直方向的大小
> step: double -> 参数t的步进值，默认为0.001，控制粒子密度
> currentT: double -> 当前渲染到的参数值，用于连续播放特效，初始值为-1.0

### 类方法
> Heart(Location origin, ParticleSpawner spawner): Heart -> 创建默认比例(1:1)的心形，周期为20tick
> Heart(double xScaleRate, double yScaleRate, Location origin, long period, ParticleSpawner spawner): Heart -> 创建自定义比例和周期的心形
> getXScaleRate(): double -> 获取X轴缩放比率
> setXScaleRate(double xScaleRate): void -> 设置X轴缩放比率
> getYScaleRate(): double -> 获取Y轴缩放比率
> setYScaleRate(double yScaleRate): void -> 设置Y轴缩放比率
> getStep(): double -> 获取步进值
> setStep(double step): void -> 设置步进值
> calculateLocations(): List<Location> -> 计算心形线上所有粒子位置
> show(): void -> 一次性显示整个心形的所有粒子
> play(): void -> 以周期性方式播放心形特效，逐渐显示整个心形
> playNextPoint(): void -> 显示心形上的下一个位置的粒子，由播放系统调用

## 实现细节
- 继承自抽象类ParticleObj，实现了Playable接口
- 使用特殊的参数方程生成心形：
  x = xScaleRate * sin(t) * cos(t) * log(|t|)
  y = yScaleRate * sqrt(|t|) * cos(t)
  其中t的范围是[-1, 1]
- 默认在xOz平面上生成心形，y坐标默认为0（注意：方程中的y实际映射到游戏中的z轴）
- 支持三种渲染模式：一次性显示、连续播放、单步播放
- 可以通过矩阵变换来调整心形的位置和形状
- 每次渲染时，通过ParticleSpawner接口生成实际的粒子效果
- 默认步进值0.001提供了较高的粒子密度，确保心形线条平滑

## 使用场景
> 创建装饰性的心形粒子特效
> 用于表达情感或友好的视觉效果
> 在游戏中实现表白、求婚等社交互动效果
> 作为生命值、恢复效果的视觉提示
> 用于节日活动（如情人节）的特殊视觉效果
> 作为复杂粒子效果系统的组成部分

## 注意事项
> 默认的步进值(0.001)非常小，会生成大量粒子，可能影响服务器性能
> 心形的大小和形状可以通过xScaleRate和yScaleRate调整
> 默认在xOz平面上生成，如需在其他平面生成需使用矩阵变换
> 播放模式下currentT会从-1逐渐增加到1，然后重置
> 心形公式是通过数学方程生成的，不同的缩放比率可能会导致形状变形
> 心形线的粒子密度在不同部分不均匀，曲率大的地方密度更高

