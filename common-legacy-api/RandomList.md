# RandomList
## 基本信息
- 类名和包路径: taboolib.common5.RandomList
- 基本用途: 基于权重的随机选择容器
- 类型: 泛型数据结构
- 所属模块: common5-legacy-api

## 类结构
### 构造函数
> RandomList(vararg element: Pair<T, Int>) -> 使用可变参数列表创建随机列表
> RandomList(element: Collection<Pair<T, Int>>) -> 使用集合创建随机列表

### 内部类
> Value<T>(val element: T, val index: Int) -> 存储元素及其权重的数据类

### 公开方法
> random(): T? -> 根据权重随机获取一个元素，不移除
> take(): T? -> 根据权重随机获取一个元素并移除
> add(element: T, weight: Int = 1) -> 添加元素及其权重
> addAll(elements: Collection<Pair<T, Int>>) -> 批量添加元素及其权重
> remove(element: T) -> 移除指定元素
> values(): MutableList<Value<T>> -> 获取所有元素及其权重
> size(): Int -> 获取元素数量
> clear() -> 清空所有元素

### 扩展函数
> Collection<Pair<T, Int>>.toRandomList(): RandomList<T> -> 将集合转换为随机列表

## 实现细节
- 使用 CopyOnWriteArrayList 作为内部存储，确保线程安全
- 随机选择算法基于权重总和，权重越高的元素被选中的概率越大
- random() 方法使用 Java 的 Random 类生成随机数
- 权重为负数或零的元素不会被随机选中
- 空列表的 random() 和 take() 方法返回 null

## 使用场景
> 实现带权重的随机抽奖系统
> 游戏中的随机掉落物品
> 基于概率的事件触发
> 随机任务或奖励分配
> 模拟不均匀分布的随机事件

## 注意事项
> 权重为零或负数的元素不会被随机选中
> 空列表的随机方法返回 null
> 使用 CopyOnWriteArrayList 可能在大量添加操作时性能较低
> 权重使用整数表示，不支持浮点数权重
> 相等的元素会被视为不同的元素，除非它们的引用相同
