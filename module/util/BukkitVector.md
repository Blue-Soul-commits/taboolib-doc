# BukkitVector
## 基本信息
- 类名和包路径: taboolib.platform.util.BukkitVector
- 基本用途: 提供Bukkit向量、位置与四元数(Quat)之间的转换工具
- 类型: Kotlin扩展函数集合
- 所属模块: bukkit-util

## 类结构
### 公开静态方法
> Quat.toVector(): org.bukkit.util.Vector -> 将四元数转换为Bukkit向量
> Quat.toLocation(world: World): org.bukkit.Location -> 将四元数转换为Bukkit位置
> Vector.toQuat(): taboolib.common5.Quat -> 将Bukkit向量转换为四元数
> Location.toQuat(): taboolib.common5.Quat -> 将Bukkit位置转换为四元数

## 实现细节
- 所有转换函数都是简单的坐标映射，不涉及复杂的数学变换
- Quat.toVector()使用四元数的x、y、z分量创建Bukkit向量
- Quat.toLocation()使用四元数的x、y、z分量和提供的世界创建Bukkit位置
- Vector.toQuat()使用Bukkit向量的x、y、z分量创建四元数
- Location.toQuat()使用Bukkit位置的x、y、z分量创建四元数
- 所有转换都使用Quat.at()静态方法创建四元数实例

## 使用场景
> 在需要进行3D数学计算时，在Bukkit API和TabooLib的四元数系统之间转换
> 在使用四元数进行旋转计算后，将结果转换回Bukkit可用的向量或位置
> 在处理实体或粒子效果的位置和方向时，利用四元数的优势进行计算
> 在3D动画或特效系统中，使用四元数进行平滑插值后转换为游戏中的位置

## 注意事项
> 这些转换只处理位置信息，不包含旋转信息(yaw和pitch)
> 四元数通常用于表示旋转，但这些转换函数只使用了四元数的位置分量
> Quat.toLocation()需要显式提供世界参数，因为四元数本身不包含世界信息
> 这些转换是纯数据转换，不会触发任何游戏事件或更新

