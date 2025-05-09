# Cube

## 基本信息
- 类名和包路径: taboolib.module.effect.shape.Cube
- 基本用途: 用于创建和渲染立方体边框的粒子特效
- 类型: 粒子特效形状类
- 所属模块: taboolib.module.effect.shape

## 类结构

### 公开静态字段
> UP: Vector -> 向上的单位向量 (0, 1, 0)
> RIGHT: Vector -> 向X正半轴的单位向量 (1, 0, 0)

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> minLoc: Location -> 立方体的一个顶点坐标
> maxLoc: Location -> 立方体的对角顶点坐标
> step: double -> 生成粒子的步进长度，控制粒子密度

### 类方法
> Cube(Location minLoc, Location maxLoc, ParticleSpawner spawner): Cube -> 创建默认步长为0.2的立方体
> Cube(Location minLoc, Location maxLoc, double step, ParticleSpawner spawner): Cube -> 创建指定步长的立方体
> getMinLocation(): Location -> 获取立方体的最小坐标点
> setMinLocation(Location minLoc): void -> 设置立方体的最小坐标点
> getMaxLocation(): Location -> 获取立方体的最大坐标点
> setMaxLocation(Location maxLoc): void -> 设置立方体的最大坐标点
> getStep(): double -> 获取步长
> setStep(double step): void -> 设置步长
> calculateLocations(): List<Location> -> 计算立方体边框上所有粒子位置
> show(): void -> 一次性显示整个立方体边框的所有粒子

## 实现细节
- 继承自抽象类ParticleObj，但未实现Playable接口，所以只支持静态显示
- 通过两个对角顶点确定一个立方体的位置和大小
- 自动计算立方体的长、宽、高以及各个边的位置
- 渲染时沿着立方体的12条边逐步生成粒子，形成完整立方体边框
- 使用向量旋转和平移操作来计算立方体的边界点
- 支持通过矩阵变换来调整立方体的位置和形状
- 每次渲染时，通过ParticleSpawner接口生成实际的粒子效果
- 立方体的原点(origin)设置为两个对角点的中点

## 使用场景
> 创建立方体区域边界的可视化效果
> 标记3D空间中的选择范围或工作区域
> 生成技能或魔法效果的边界框
> 用于显示方块选择或建筑区域
> 创建房间、容器等立方体结构的粒子轮廓
> 作为游戏规则中区域边界的视觉提示

## 注意事项
> 必须确保两个位置参数在同一个世界中，否则会抛出异常
> 不支持动态播放(play)功能，因为未实现Playable接口
> 立方体只渲染边框，不会填充内部空间
> 当立方体尺寸过大或步长过小时，会生成大量粒子，可能影响服务器性能
> 可以通过setIncrement系列方法调整立方体的位置偏移
> 构造时自动处理最大最小坐标，不需要特定顺序提供坐标点
