# NodeReader
## 基本信息
- 类名和包路径: taboolib.module.navigation.NodeReader
- 基本用途: 负责读取和管理寻路系统中的节点，处理地形分析和节点生成
- 类型: 开放类
- 所属模块: bukkit-navigation

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> entity: NodeEntity -> 与此节点读取器关联的实体
> nodes: HashMap<Int, Node> -> 存储已生成节点的哈希表，键为节点哈希值
> type: HashMap<Long, PathType> -> 缓存方块位置与路径类型的映射
> typeGetter: PathTypeFactory -> 路径类型工厂，用于获取方块的路径类型
> world: World -> 实体所在的世界

### 类方法
> done(): Unit -> 清理节点和类型缓存
> getGoal(x: Double, y: Double, z: Double): NodeTarget -> 获取目标节点
> getNode(position: Vector): Node -> 获取指定位置的节点
> getNode(x: Int, y: Int, z: Int): Node -> 获取指定坐标的节点
> getCachedBlockType(x: Int, y: Int, z: Int): PathType -> 获取缓存的方块路径类型
> getCachedBlockType(position: Vector): PathType -> 获取缓存的方块路径类型
> getStart(): Node -> 获取起始节点
> getLandHeight(position: Vector): Double -> 获取指定位置的陆地高度
> getLandNode(x: Int, y: Int, z: Int): Node? -> 获取陆地节点
> hasPositiveMalus(position: Vector): Boolean -> 检查实体是否可以通过指定位置
> isNeighborValid(neighbor: Node?, node: Node): Boolean -> 检查相邻节点是否有效
> isDiagonalValid(diagonal: Node, nodeLeft: Node?, nodeRight: Node?, node: Node?): Boolean -> 检查对角线节点是否有效
> getNeighbors(nodes: Array<Node?>, node: Node): Int -> 获取节点的相邻节点

## 实现细节
- 使用哈希表缓存节点和方块类型，避免重复创建
- 提供复杂的地形分析逻辑，处理不同类型的地形（如水、空气、栅栏等）
- 支持实体特性（如漂浮、空气供应等）对寻路的影响
- 实现八方向移动（上下左右及对角线）的节点连接
- 考虑高度差异和方块类型对路径可行性的影响
- 使用 PathTypeFactory 获取方块的路径类型，并根据实体特性计算通行代价

## 使用场景
> 在 PathFinder 中用于生成和管理寻路节点
> 分析地形和障碍物，确定可行走路径
> 根据实体特性（如大小、能否漂浮）调整寻路行为
> 处理特殊地形如水域、高度差、栅栏等的通行逻辑

## 注意事项
> 节点生成和类型判断是寻路系统的性能瓶颈，应合理使用缓存
> 代码中包含一些被注释的逻辑，可能是未完成或已弃用的功能
> 方向标记（如"东"、"西"等）与实际方向有混淆，需注意代码中的实际实现
> 高度差判断使用硬编码阈值 1.25，可能需要根据实体类型调整

