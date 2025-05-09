# NodeEntity
## 基本信息
- 类名和包路径: taboolib.module.navigation.NodeEntity
- 基本用途: 表示寻路系统中的实体，提供实体属性和行为的抽象
- 类型: 开放类
- 所属模块: bukkit-navigation

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> location: Location -> 实体的位置
> height: Double -> 实体的高度
> width: Double -> 实体的宽度，默认为 1.0
> depth: Double -> 实体的深度，默认与宽度相同
> canPassDoors: Boolean -> 是否可以通过门，默认为 true
> canOpenDoors: Boolean -> 是否可以打开门，默认为 false
> canFloat: Boolean -> 是否可以漂浮，默认为 true
> random: Random -> 随机数生成器，用于随机行为
> restrictCenter: Vector -> 活动范围的中心点，默认为原点
> restrictRadius: Float -> 活动范围的半径，默认为 -1f（无限制）
> hasRestriction: Boolean -> 是否有活动范围限制
> x: Double -> 实体的 X 坐标
> y: Double -> 实体的 Y 坐标
> z: Double -> 实体的 Z 坐标
> boundingBox: BoundingBox -> 实体的碰撞箱
> pathfindingMalus: EnumMap<PathType, Float> -> 不同路径类型的通行代价修正值

### 类方法
> getPathfindingMalus(pathType: PathType): Float -> 获取指定路径类型的通行代价修正值
> setPathfindingMalus(pathType: PathType, malus: Float): Unit -> 设置指定路径类型的通行代价修正值
> isWithinRestriction(): Boolean -> 检查实体是否在活动范围内
> isWithinRestriction(pos: Vector): Boolean -> 检查指定位置是否在活动范围内
> getWalkTargetValue(pos: Vector): Double -> 获取指定位置的行走目标值
> getWalkTargetValue(pos: Vector, world: World): Double -> 获取指定位置和世界的行走目标值
> restrictTo(pos: Vector, radius: Int): Unit -> 设置实体的活动范围
> canCutCorner(pathType: PathType): Boolean -> 检查是否可以切过指定路径类型的角落
> canStandOnFluid(fluid: Fluid): Boolean -> 检查是否可以站在指定流体上
> isInWater(): Boolean -> 检查实体是否在水中
> isOnGround(): Boolean -> 检查实体是否在地面上
> getAirSupply(): Int -> 获取实体的空气供应量

## 实现细节
- 使用 Location 对象表示实体位置，提供 x、y、z 属性的便捷访问
- 自动根据实体位置和尺寸计算碰撞箱
- 使用 EnumMap 存储不同路径类型的通行代价修正值
- 提供活动范围限制功能，可以限制实体在特定区域内移动
- 默认实现了基本的环境检测方法，如是否在水中、是否在地面上等
- 大多数方法设计为可重写，允许子类定制行为

## 使用场景
> 作为寻路系统中的实体抽象，提供实体属性和行为
> 在 PathFinder 和 NodeReader 中用于计算路径和节点
> 自定义 AI 实体的移动和寻路行为
> 模拟不同类型实体（如飞行、游泳、陆行）的寻路特性

## 注意事项
> getWalkTargetValue 方法默认返回 -1.0，子类重写时不应返回 -1 值，否则会影响随机游荡算法
> 碰撞箱计算假设实体中心点在 location 的 x 和 z 坐标上，底部在 y 坐标上
> 大多数布尔属性（如 canFloat、canPassDoors）默认值可能需要根据实际实体类型调整
> 活动范围限制功能需要手动调用 restrictTo 方法设置
