# TwoDProjector

## 基本信息
- 类名和包路径: taboolib.module.effect.utils.TwoDProjector
- 基本用途: 提供二维至三维投影功能，将二维坐标投影到三维空间
- 类型: 工具类
- 所属模块: taboolib.module.effect.utils

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> create2DProjector(loc: Location, n: Vector): BiFunction<Double, Double, Location> -> 创建一个二维至三维投影函数

### 类内可被访问字段
> origin: Location -> 投影的原点
> n1: Vector -> 投影平面的第一个基向量
> n2: Vector -> 投影平面的第二个基向量

### 类方法
> TwoDProjector(origin: Location, n: Vector) -> 构造函数，创建一个二维投影器
> apply(x: double, y: double): Location -> 将给定的二维坐标投影到三维空间

## 实现细节
- 构造函数接收一个原点和一个法向量，并计算投影平面的两个基向量
- 基向量n1通过法向量n与临时向量t的叉积计算得出，并进行了归一化处理
- 基向量n2通过n1与法向量n的叉积计算得出，并进行了归一化处理
- create2DProjector静态方法提供了一种函数式编程的方式来创建投影器，返回一个接收二维坐标并返回三维位置的函数
- apply方法将输入的二维坐标通过两个基向量进行线性组合，形成投影后的向量，再将结果添加到原点上得到最终位置

## 使用场景
> 创建平面粒子效果，如将2D图形投影到游戏世界的3D空间
> 实现UI元素、信息展示板等需要在空间中显示平面内容的场景
> 粒子动画效果，将二维坐标系中的动画轨迹投影到三维空间

## 注意事项
> 算法由@Bryan33提供
> 投影平面是由原点和法向量决定的
> 投影结果受原点位置和法向量方向的影响
> apply方法返回的是新的Location对象，不会修改原始坐标
> 类提供了两种使用方式：通过构造器创建实例，或通过静态方法create2DProjector获取函数
