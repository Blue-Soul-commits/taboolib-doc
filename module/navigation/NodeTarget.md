# NodeTarget
## 基本信息
- 类名和包路径: taboolib.module.navigation.NodeTarget
- 基本用途: 表示寻路系统中的目标节点，用于 A* 算法中的目标追踪和启发式计算
- 类型: 类
- 所属模块: bukkit-navigation

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> bestHeuristic: Float -> 记录到目标的最佳启发式估值，初始值为最大浮点数
> bestNode: Node? -> 记录到目标的最佳节点，初始为 null
> reached: Boolean -> 标记目标是否已被到达，初始为 false

### 类方法
> updateBest(bestHeuristic: Float, node: Node?): Unit -> 更新最佳启发式估值和对应节点
> setReached(): Unit -> 标记目标已被到达

## 实现细节
- 继承自 Node 类，保留了基础节点的所有功能
- 通过构造函数接收一个 Node 对象，并使用其坐标初始化
- bestHeuristic 初始值设为极大值 (3.4028235E38f)，确保首次比较时能被更新
- 提供 updateBest 方法用于在寻路过程中更新最佳启发式估值和对应节点
- 使用 private set 修饰符保护 bestHeuristic 和 bestNode 字段，只能通过 updateBest 方法修改

## 使用场景
> 在 A* 寻路算法中表示目标位置
> 在 PathFinder 类中用于追踪到目标的最佳路径
> 在多目标寻路中作为可能的目标点之一
> 在启发式搜索中记录和更新最佳路径信息

## 注意事项
> bestHeuristic 初始值为浮点数最大值，确保首次比较时能被更新
> updateBest 方法只在找到更好的启发式值时才更新
> reached 字段需要手动调用 setReached 方法设置
> 作为 Node 的子类，继承了所有节点的基本功能和属性
