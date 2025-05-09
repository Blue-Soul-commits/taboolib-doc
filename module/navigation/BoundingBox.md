# BoundingBox
## 基本信息
- 类名和包路径: taboolib.module.navigation.BoundingBox
- 基本用途: 表示三维空间中的轴对齐包围盒，用于碰撞检测和空间计算
- 类型: 数据类
- 所属模块: bukkit-navigation

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> zero(): BoundingBox -> 创建一个位于原点且大小为零的包围盒

### 类内可被访问字段
> minX: Double -> 包围盒在 X 轴的最小坐标
> minY: Double -> 包围盒在 Y 轴的最小坐标
> minZ: Double -> 包围盒在 Z 轴的最小坐标
> maxX: Double -> 包围盒在 X 轴的最大坐标
> maxY: Double -> 包围盒在 Y 轴的最大坐标
> maxZ: Double -> 包围盒在 Z 轴的最大坐标

### 类方法
> move(vector: Vector): BoundingBox -> 按指定向量移动包围盒并返回新实例
> move(x: Double, y: Double, z: Double): BoundingBox -> 按指定坐标偏移量移动包围盒并返回新实例
> contains(v: Vector): Boolean -> 检查包围盒是否包含指定向量点
> contains(x: Double, y: Double, z: Double): Boolean -> 检查包围盒是否包含指定坐标点
> contains(other: BoundingBox): Boolean -> 检查包围盒是否完全包含另一个包围盒
> contains(min: Vector, max: Vector): Boolean -> 检查包围盒是否包含由两个向量定义的空间
> contains(minX: Double, minY: Double, minZ: Double, maxX: Double, maxY: Double, maxZ: Double): Boolean -> 检查包围盒是否包含由六个坐标定义的空间
> getSize(): Double -> 获取包围盒的平均尺寸（三个轴向尺寸的平均值）
> getXSize(): Double -> 获取包围盒在 X 轴方向的尺寸
> getYSize(): Double -> 获取包围盒在 Y 轴方向的尺寸
> getZSize(): Double -> 获取包围盒在 Z 轴方向的尺寸

## 实现细节
- 使用 Kotlin 的 data class 实现，提供了自动生成的 equals、hashCode 和 copy 方法
- 提供了多种重载的 contains 方法，用于检测点、向量和其他包围盒是否在当前包围盒内
- move 方法返回新的包围盒实例，而不是修改当前实例，符合不可变对象设计模式
- 使用 Kotlin 的 min 和 max 函数确保在处理向量时正确计算包围盒的边界

## 使用场景
> 在寻路系统中表示实体的碰撞箱
> 在碰撞检测中判断实体是否与其他物体相交
> 在空间划分算法中表示区域边界
> 在物理模拟中表示物体的边界

## 注意事项
> contains 方法对于点的检测使用半开区间 [min, max)，即包含最小边界但不包含最大边界
> contains 方法对于包围盒的检测使用闭区间 [min, max]，即完全包含另一个包围盒
> 作为不可变对象，所有修改操作（如 move）都会返回新实例，不会修改原对象

