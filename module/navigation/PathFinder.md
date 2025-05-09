# PathFinder
## 基本信息
- 类名和包路径: taboolib.module.navigation.PathFinder
- 基本用途: 实现 A* 寻路算法，用于计算从起点到目标的最佳路径
- 类型: 类
- 所属模块: bukkit-navigation

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> nodeReader: NodeReader -> 节点读取器，用于获取和管理寻路节点
> neighbors: Array<Node?> -> 存储相邻节点的数组，大小为 32
> openSet: BinaryHeap -> 二叉堆实现的开放列表，用于 A* 算法

### 类方法
> findPath(position: Location, distance: Float, distanceManhattan: Int = 1, deep: Float = 1f): Path? -> 寻找从当前位置到指定位置的路径
> findPath(position: Vector, distance: Float, distanceManhattan: Int = 1, deep: Float = 1f): Path? -> 寻找从当前位置到指定向量的路径
> findPath(position: Set<Vector>, distance: Float, distanceManhattan: Int = 1, deep: Float = 1f): Path? -> 寻找从当前位置到多个目标中最优目标的路径
> findPath(begin: Node, list: List<Pair<NodeTarget, Vector>>, distance: Float, distanceManhattan: Int, deep: Float): Path? -> 私有方法，实现 A* 寻路算法的核心逻辑
> getBestHeuristic(node: Node, list: List<Pair<NodeTarget, Vector>>): Float -> 私有方法，计算节点到目标的最佳启发式估值
> reconstructPath(node: Node, position: Vector, flag: Boolean): Path -> 私有方法，从目标节点回溯构建完整路径

## 实现细节
- 基于 A* 算法实现，使用二叉堆优化开放列表操作
- 支持单目标和多目标寻路，可以寻找到多个目标中最优的一个
- 使用曼哈顿距离作为到达目标的判断标准，可通过参数调整
- 提供搜索深度和距离限制参数，防止无限搜索
- 使用启发式函数优化搜索方向，加快寻路速度
- 在寻路完成后自动清理节点缓存，释放内存

## 使用场景
> 实体 AI 系统中的路径规划
> 自动寻路导航系统
> 多目标选择中寻找最优目标
> 地形分析和可达性检测

## 注意事项
> distance 参数限制了搜索范围，过小可能找不到路径，过大会增加计算量
> distanceManhattan 参数决定了到达目标的判定距离，通常为 1
> deep 参数影响最大搜索次数，增大可以搜索更复杂的路径，但会增加计算量
> 寻路结果可能为 null，表示无法找到有效路径
> 寻路完成后会自动调用 nodeReader.done() 清理缓存
