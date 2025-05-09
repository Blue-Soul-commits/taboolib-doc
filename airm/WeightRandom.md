# WeightRandom

## 基本信息
- 类名和包路径: top.maplex.arim.tools.weightrandom.WeightRandom
- 基本用途: 提供基于权重的随机选择功能，允许按照不同权重值随机选择集合中的元素
- 类型: 具体类和扩展函数
- 所属模块: 权重随机工具模块

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> 无类内可被访问字段

### 类方法
> getWeightRandom(categories: Collection<WeightCategory<T>>): T? -> 直接返回随机选择的类别对象
> getRandom(categories: Collection<T>, processing: (T) -> Int): WeightCategory<T>? -> 根据处理函数计算权重并随机选择
> getRandom(categories: Collection<WeightCategory<T>>): WeightCategory<T>? -> 核心随机选择方法

### 扩展函数
> Collection<T>.randomWeight(processing: (T) -> Int): WeightRandom.WeightCategory<T>? -> 集合扩展函数，返回随机选择的带权重类别
> Collection<T>.randomWeightValue(processing: (T) -> Int): T? -> 集合扩展函数，返回随机选择的元素值

### 内部类
> WeightCategory<T>(category: T, weight: Int) -> 包含类别和权重的数据类

## 实现细节
- 使用权重总和作为随机数生成的上限，生成一个随机数
- 遍历集合，累加权重，当累加值超过随机数时选中当前元素
- 支持两种使用方式：
  1. 直接使用WeightCategory对象集合
  2. 使用普通集合配合计算权重的函数
- 提供了便捷的集合扩展函数，可直接在任何集合上调用
- 如果权重总和小于或等于0，返回null
- 使用TabooLib的random()函数生成随机数
- 通过Arim.weightRandom全局实例实现扩展函数

## 使用场景
> 实现带权重的随机奖励系统，不同物品有不同的掉落概率
> 随机生成带有不同稀有度的物品，稀有度越高权重越低
> 实现带有多个概率分支的任务或事件系统
> 在NPC对话或游戏剧情中实现基于权重的随机反应
> 战斗系统中的随机暴击或特殊效果，基于不同的触发权重

## 注意事项
> 权重必须为正整数，否则可能导致不可预期的结果
> 如果所有权重之和小于或等于0，方法将返回null
> 权重是相对的，即元素被选中的概率为其权重除以权重总和
> 扩展函数依赖于Arim类中的weightRandom实例，需确保其已正确初始化
> 使用lambda表达式计算权重可能会对性能产生影响，特别是对大型集合
