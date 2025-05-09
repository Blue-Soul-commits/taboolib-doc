# RandomPositionGenerator
## 基本信息
- 类名和包路径: taboolib.module.navigation.RandomPositionGenerator
- 基本用途: 提供生成随机位置的工具，用于实体 AI 的随机移动和寻路
- 类型: 单例对象
- 所属模块: bukkit-navigation

## 类结构
### 公开静态字段
> PI_OF_TWO: Double -> π/2 的近似值，用于角度计算
> SQRT_OF_TWO: Double -> √2 的近似值，用于距离计算

### 公开静态方法
> generateLand(nodeEntity: NodeEntity, restrictX: Int, restrictY: Int): Vector? -> 生成地面随机坐标
> generateLandAbove(nodeEntity: NodeEntity, restrictX: Int, restrictY: Int): Vector? -> 生成地面之上的随机坐标
> generateLandAbove(nodeEntity: NodeEntity, restrictX: Int, restrictY: Int, start: Vector): Vector? -> 从指定起点生成地面之上的随机坐标
> generateLandTowards(nodeEntity: NodeEntity, restrictX: Int, restrictY: Int, target: Vector): Vector? -> 生成朝向目标的地面随机坐标
> generateAirTowards(nodeEntity: NodeEntity, restrictX: Int, restrictY: Int, target: Vector): Vector? -> 生成朝向目标的空中随机坐标
> generateLandAvoid(nodeEntity: NodeEntity, restrictX: Int, restrictY: Int, start: Vector): Vector? -> 生成远离起点的地面随机坐标
> generate(nodeEntity: NodeEntity, rX: Int, yY: Int, start: Vector?, onWater: Boolean, aboveLand: Boolean, requireWalkable: Boolean): Vector? -> 生成随机坐标的核心方法
> moveUp(position: Vector, y: Int, maxY: Int, check: (Vector) -> Boolean): Vector -> 通过条件不断向上移动坐标指针

### 类内可被访问字段
> 无

### 类方法
> randomDelta(random: Random, restrictX: Int, restrictY: Int, vector: Vector?): Vector? -> 私有方法，计算随机偏移量

## 实现细节
- 使用 Kotlin 的 object 关键字实现单例模式
- 提供多种生成随机位置的方法，适用于不同场景（地面、空中、朝向目标、远离起点等）
- 考虑实体的活动范围限制，确保生成的位置在限制范围内
- 使用 PathTypeFactory 检查位置的可行走性，确保生成的位置是实体可到达的
- 支持在水上、地面上或空中生成位置
- 使用三角函数计算朝向特定方向的随机偏移
- 通过 moveUp 方法处理垂直方向的位置调整，确保生成的位置在有效高度

## 使用场景
> 实体 AI 系统中的随机游荡行为
> 寻找逃跑或躲避的随机位置
> 生成朝向目标但不完全相同的随机位置
> 寻找远离危险区域的安全位置
> 在复杂地形中找到可行走的随机位置

## 注意事项
> 生成的位置可能为 null，表示无法找到满足条件的随机位置
> restrictX 和 restrictY 参数控制随机范围，过大会增加计算量，过小可能找不到有效位置
> 默认尝试 10 次生成随机位置，如果都失败则返回 null
> 生成位置时会考虑实体的 getWalkTargetValue 方法返回值，该方法应根据实体特性正确实现
> 使用 bottomCenter 方法确保返回的位置在方块中心
