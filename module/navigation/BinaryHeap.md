# BinaryHeap
## 基本信息
- 类名和包路径: taboolib.module.navigation.BinaryHeap
- 基本用途: 实现二叉堆数据结构，用于寻路算法中的优先队列
- 类型: 工具类
- 所属模块: bukkit-navigation

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> heap: Array<Node?> -> 存储节点的数组，初始大小为128
> size: Int -> 当前堆中的节点数量

### 类方法
> insert(node: Node): Node -> 将节点插入堆中并返回该节点
> clear(): Unit -> 清空堆
> pop(): Node -> 弹出并返回堆顶节点（最小代价节点）
> changeCost(node: Node, value: Float): Unit -> 更改节点的代价值并调整堆结构
> upHeap(value: Int): Unit -> 向上调整堆，用于插入操作和减小代价时
> downHeap(value: Int): Unit -> 向下调整堆，用于弹出操作和增加代价时
> isEmpty(): Boolean -> 检查堆是否为空

## 实现细节
- 使用数组实现二叉最小堆，堆顶元素具有最小的代价值
- 当数组容量不足时，会自动扩容为原来的两倍
- 通过 Node 类的 heapIdx 属性跟踪节点在堆中的位置
- 使用 actualCost 属性作为节点在堆中的排序依据
- 插入和弹出操作的时间复杂度为 O(log n)
- 支持动态调整节点代价并重新平衡堆结构

## 使用场景
> 在 A* 寻路算法中作为开放列表，高效管理待探索的节点
> 在 Dijkstra 算法中用于选择最短路径
> 在 PathFinder 类中用于实现高效的路径查找
> 需要频繁获取最小代价元素的场景

## 注意事项
> 插入已在堆中的节点会抛出 IllegalStateException 异常
> 节点的 heapIdx 属性由堆自动管理，不应手动修改
> 修改节点代价后必须调用 changeCost 方法以维护堆的正确性
> 弹出操作会将节点的 heapIdx 设为 -1，表示节点不再在堆中
