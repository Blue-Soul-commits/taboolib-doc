# Node
## 基本信息
- 类名和包路径: taboolib.module.navigation.Node
- 基本用途: 表示寻路系统中的路径节点，用于 A* 算法实现
- 类型: 开放类
- 所属模块: bukkit-navigation

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> createHash(x: Int, y: Int, z: Int): Int -> 根据坐标创建唯一的哈希值，用于节点标识和比较

### 类内可被访问字段
> x: Int -> 节点的 X 坐标
> y: Int -> 节点的 Y 坐标
> z: Int -> 节点的 Z 坐标
> hash: Int -> 节点的哈希值，基于坐标计算
> heapIdx: Int -> 节点在二叉堆中的索引，-1 表示不在开放列表中
> actualCost: Float -> 从起点到当前节点的实际代价（g 值）
> totalCost: Float -> 估计的总代价（h 值）
> cost: Float -> 节点的综合代价（f 值 = g + h）
> parent: Node? -> 父节点，用于重建路径
> isClosed: Boolean -> 节点是否已关闭（在关闭列表中）
> walkedDistance: Float -> 已走过的距离
> costMalus: Float -> 代价惩罚，影响节点的通行难度
> type: PathType -> 节点的路径类型，默认为 BLOCKED

### 类方法
> cloneAndMove(x: Int, y: Int, z: Int): Node -> 克隆当前节点并移动到新坐标
> distanceTo(node: Node): Float -> 计算到另一个节点的欧几里得距离
> distanceToSqr(node: Node): Float -> 计算到另一个节点的欧几里得距离的平方
> distanceManhattan(node: Node): Float -> 计算到另一个节点的曼哈顿距离
> distanceManhattan(position: Vector): Float -> 计算到指定向量位置的曼哈顿距离
> asBlockPos(): Vector -> 将节点坐标转换为 Vector 对象
> inOpenSet(): Boolean -> 检查节点是否在开放列表中
> display(world: World): Unit -> 在指定世界中显示节点的粒子效果
> display(player: Player): Unit -> 向指定玩家显示节点的粒子效果
> equals(other: Any?): Boolean -> 比较两个节点是否相等
> hashCode(): Int -> 获取节点的哈希码
> toString(): String -> 获取节点的字符串表示

## 实现细节
- 基于整数坐标系统表示三维空间中的位置
- 使用自定义哈希算法确保节点的唯一性和快速比较
- 支持多种距离计算方法，适用于不同的寻路启发式算法
- 提供节点可视化功能，便于调试和展示
- 实现了标准的 equals 和 hashCode 方法，支持在集合中使用
- 通过 heapIdx 字段跟踪节点在二叉堆中的位置，优化寻路算法性能

## 使用场景
> 在 A* 寻路算法中表示路径上的节点
> 在 PathFinder 类中用于构建和优化路径
> 在实体 AI 系统中用于导航决策
> 在路径可视化和调试中展示寻路过程

## 注意事项
> 节点坐标使用整数表示，对应 Minecraft 的方块坐标系统
> 多个代价相关字段（actualCost, totalCost, cost）在寻路算法中有不同用途
> 节点类型默认为 BLOCKED，需要在寻路过程中根据实际情况设置
> 使用 cloneAndMove 方法创建新节点时会保留原节点的所有属性
