# Path
## 基本信息
- 类名和包路径: taboolib.module.navigation.Path
- 基本用途: 表示寻路系统中的完整路径，包含从起点到终点的一系列节点
- 类型: 类
- 所属模块: bukkit-navigation

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> nodes: MutableList<Node> -> 路径中的所有节点列表
> target: Vector -> 路径的目标位置
> reached: Boolean -> 标记是否成功到达目标
> openSet: Array<Node?> -> 空数组，可能用于调试或记录寻路过程中的开放列表
> closeSet: Array<Node?> -> 空数组，可能用于调试或记录寻路过程中的关闭列表
> distToTarget: Float -> 路径终点到目标的曼哈顿距离
> nextNodeIndex: Int -> 当前遍历到的节点索引，用于路径跟踪

### 类方法
> getNextIndex(): Int -> 获取当前节点索引
> hasNext(): Boolean -> 检查是否还有下一个节点
> advance(): Unit -> 前进到下一个节点
> notStarted(): Boolean -> 检查是否尚未开始遍历
> isDone(): Boolean -> 检查是否已完成遍历
> getFinalPoint(): Node? -> 获取路径的最终节点
> getEndNode(): Node? -> 获取路径的最终节点
> getNode(i: Int): Node -> 获取指定索引的节点
> truncateNode(i: Int): Unit -> 从指定索引处截断路径
> replaceNode(i: Int, node: Node): Unit -> 替换指定索引处的节点
> getNodeCount(): Int -> 获取路径中的节点数量
> getEntityPosAtNode(nodeEntity: NodeEntity, i: Int): Vector -> 获取实体在指定节点处的位置
> getNodePos(i: Int): Vector -> 获取指定节点的位置向量
> getNextEntityPos(entity: NodeEntity): Vector -> 获取实体在下一节点处的位置
> getNextNodePos(): Vector -> 获取下一节点的位置向量
> getNextNode(): Node -> 获取下一节点
> getPreviousNode(): Node? -> 获取前一节点
> sameAs(path: Path?): Boolean -> 检查与另一路径是否相同
> canReach(): Boolean -> 检查是否可以到达目标

## 实现细节
- 使用可变列表存储路径节点，支持动态修改路径
- 提供路径遍历功能，通过 nextNodeIndex 跟踪当前位置
- 支持路径比较、截断和替换操作
- 计算实体在路径上的精确位置，考虑实体宽度
- 使用 @Suppress("CanBeParameter") 注解抑制编译器警告

## 使用场景
> 在寻路系统中表示计算出的完整路径
> 在实体 AI 中用于导航和移动控制
> 在路径跟踪中逐步遍历节点
> 在路径优化中修改或截断现有路径

## 注意事项
> 路径节点索引从 0 开始，使用前应检查索引有效性
> 使用 advance() 方法前进路径时不会自动检查边界
> openSet 和 closeSet 字段为空数组，可能仅用于兼容性目的
> 路径比较 sameAs() 方法仅检查节点坐标，不比较其他属性