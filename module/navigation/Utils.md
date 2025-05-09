# Utils
## 基本信息
- 类名和包路径: taboolib.module.navigation.Utils
- 基本用途: 提供寻路系统中常用的工具函数和扩展方法
- 类型: Kotlin 扩展函数文件
- 所属模块: bukkit-navigation

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> createPathfinder(nodeEntity: NodeEntity): PathFinder -> 创建路径查找器实例

### 类内可被访问字段
> 无

### 类方法
> World.getBlockAt(position: Vector): Block -> 获取指定向量位置的方块
> World.getBlockAtIfLoaded(position: Vector): Block? -> 获取指定向量位置的方块，仅当区块已加载时
> Vector.toBlock(world: World): Block -> 将向量转换为世界中的方块
> Vector.down(): Vector -> 获取向下一格的向量
> Vector.up(): Vector -> 获取向上一格的向量
> Vector.hash(): Long -> 计算向量的哈希值
> Vector.set(x: Int, y: Int, z: Int): Vector -> 设置向量的整数坐标
> Vector.set(x: Double, y: Double, z: Double): Vector -> 设置向量的浮点坐标（向下取整）
> Vector.distSqr(double1: Double, double2: Double, double3: Double, boolean4: Boolean): Double -> 计算到指定坐标的距离平方
> Vector.distSqr(position: Vector): Double -> 计算到另一个向量的距离平方
> Vector.distSqr(position: Vector, boolean2: Boolean): Double -> 计算到另一个向量的距离平方，可选是否考虑中心点
> Vector.bottomCenter(): Vector -> 获取方块底部中心的向量
> Vector.closerThan(position: Vector, double2: Double): Boolean -> 检查是否比指定距离更近
> Location.toCommonVector(): Vector -> 将位置转换为整数坐标的向量
> Block.isDoor(): Boolean -> 检查方块是否为门
> Block.isIronDoor(): Boolean -> 检查方块是否为铁门
> Block.isClimbable(): Boolean -> 检查方块是否可攀爬
> Block.isOpened(): Boolean -> 检查门是否打开
> Material.isAirLegacy(): Boolean -> 检查材质是否为空气（兼容旧版本）
> Material.isWater(): Boolean -> 检查材质是否为水

## 实现细节
- 提供大量扩展函数，简化寻路系统中的常见操作
- 使用位运算和位移操作优化哈希值计算
- 提供跨版本兼容的方法，处理不同 Minecraft 版本的 API 差异
- 使用 NumberConversions 处理数值转换，确保一致性
- 通过字符串匹配处理材质名称的差异，提高兼容性

## 使用场景
> 在寻路系统中简化向量和方块操作
> 处理不同 Minecraft 版本的 API 差异
> 计算距离和位置关系
> 检测特殊方块类型（门、梯子等）
> 创建和使用路径查找器

## 注意事项
> 某些方法依赖于方块或材质的命名规则，可能在未来版本中需要更新
> isOpened() 方法根据 Minecraft 版本使用不同的实现
> getBlockAtIfLoaded() 方法在区块未加载时返回 null，调用前应检查返回值
> 使用 hash() 方法时应注意可能的哈希冲突
> 某些方法使用了 @Suppress("DEPRECATION") 注解，表示使用了已弃用的 API

