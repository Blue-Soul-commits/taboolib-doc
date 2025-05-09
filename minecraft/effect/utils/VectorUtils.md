# VectorUtils

## 基本信息
- 类名和包路径: taboolib.module.effect.utils.VectorUtils
- 基本用途: 提供向量操作的工具方法，特别是向量旋转相关的功能
- 类型: 工具类
- 所属模块: taboolib.module.effect.utils

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> createVector(start: Location, end: Location): Vector -> 通过两点创建向量，减少额外克隆的损耗
> rotateAroundAxisX(v: Vector, angle: double): Vector -> 将给定向量绕X轴进行旋转
> rotateAroundAxisY(v: Vector, angle: double): Vector -> 将给定向量绕Y轴进行旋转
> rotateAroundAxisZ(v: Vector, angle: double): Vector -> 将给定向量绕Z轴进行旋转
> rotateVector(v: Vector, yawDegrees: float, pitchDegrees: float): Vector -> 使用yaw和pitch角度旋转向量，适用于非单位向量
> isNormalized(vector: Vector): boolean -> 判断一个向量是否已单位化
> rotateAroundAxis(vector: Vector, axis: Vector, angle: double): Vector -> 空间向量绕任一向量旋转
> rotateAroundNonUnitAxis(vector: Vector, axis: Vector, angle: double): Vector -> 空间向量绕非单位向量旋转，使用罗德里格旋转公式

### 类内可被访问字段
> 无类内可被访问字段

### 类方法
> 无实例方法

## 实现细节
- createVector方法直接使用坐标相减来创建向量，避免了Location克隆带来的性能损失
- rotateAroundAxisX/Y/Z方法使用旋转矩阵实现向量绕坐标轴的旋转
- rotateVector方法使用yaw和pitch角度实现向量的旋转，适用于非单位向量
- isNormalized方法通过检查向量长度平方是否接近1来判断向量是否单位化
- rotateAroundAxis方法先检查旋转轴是否单位化，如果不是则先进行单位化再调用rotateAroundNonUnitAxis
- rotateAroundNonUnitAxis方法使用罗德里格旋转公式实现向量绕任意轴的旋转

## 使用场景
> 粒子效果中的向量操作，如旋转、平移等
> 3D空间中物体的旋转变换
> 位置计算，如从一个点到另一个点的向量
> 复杂粒子效果的数学计算
> 自定义实体或物体的运动轨迹计算

## 注意事项
> 旋转方法中的角度参数使用度数表示，内部会转换为弧度进行计算
> rotateAroundAxisY方法中的角度取反，这可能是为了符合游戏中的坐标系统
> rotateAroundNonUnitAxis方法要求旋转轴必须是单位向量，否则结果可能不正确
> 大多数方法会直接修改传入的向量对象，而不是创建新的向量对象
> rotateVector方法中的实现来自SexyToad，专门处理非单位向量的旋转
