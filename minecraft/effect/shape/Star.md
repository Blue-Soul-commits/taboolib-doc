# Star

## 基本信息
- 类名和包路径: taboolib.module.effect.shape.Star
- 基本用途: 用于创建和渲染五角星粒子特效
- 类型: 粒子特效形状类
- 所属模块: taboolib.module.effect.shape

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> radius: double -> 五角星的半径（从中心到顶点的距离）
> step: double -> 每个粒子之间的间隔（步长）
> length: double -> 每条边的长度，根据半径自动计算
> currentSide: int -> 当前渲染到的边，用于连续播放特效
> currentStep: double -> 当前渲染到边上的位置，用于连续播放特效
> changeableStart: Vector -> 可变的起始向量，用于播放时动态计算
> changeableEnd: Location -> 可变的结束位置，用于播放时动态计算

### 类方法
> Star(Location origin, ParticleSpawner spawner): Star -> 创建默认参数(半径1，步长0.05)的五角星
> Star(Location origin, double radius, double step, long period, ParticleSpawner spawner): Star -> 创建指定半径、步长和周期的五角星
> calculateLocations(): List<Location> -> 计算五角星上所有粒子位置
> show(): void -> 一次性显示整个五角星的所有粒子
> play(): void -> 以周期性方式播放五角星特效，逐边绘制
> playNextPoint(): void -> 显示五角星上的下一个位置的粒子，由播放系统调用

## 实现细节
- 继承自抽象类ParticleObj，实现了Playable接口
- 五角星由5条相等的线段组成，各线段以中心点为原点，旋转144度角分布
- 算法通过向量计算和旋转生成五角星：
  - 首先确定第一个顶点位置
  - 使用固定旋转角度(144度)计算其他顶点
  - 连接顶点形成五角星
- 每条边的长度根据半径和几何关系自动计算：length = 2 * radius * cos(36°)
- 支持三种渲染模式：一次性显示、连续播放、单步播放
- 播放模式下会逐边绘制五角星，绘制完一条边后旋转到下一条边
- 可以通过矩阵变换来调整五角星的位置和形状
- 每次渲染时，通过ParticleSpawner接口生成实际的粒子效果

## 使用场景
> 创建五角星形粒子特效和装饰
> 用于魔法、召唤等游戏元素的视觉效果
> 作为成就、奖励或特殊状态的视觉提示
> 标记重要位置或区域
> 作为复杂粒子效果系统的组成部分
> 实现评分系统的视觉展示

## 注意事项
> 五角星的形状固定为正五角星，无法自定义角数
> 如需自定义角数的星形，应使用NStar类
> 当半径过大或步长过小时，会生成大量粒子，可能影响服务器性能
> 默认在xOz平面上生成，如需在其他平面生成需使用矩阵变换
> 播放模式下逐边绘制，当所有边绘制完成后会停止
> 默认周期为20tick，可根据需要调整播放速度
