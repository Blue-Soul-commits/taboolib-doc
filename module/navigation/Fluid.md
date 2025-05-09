# Fluid
## 基本信息
- 类名和包路径: taboolib.module.navigation.Fluid
- 基本用途: 表示 Minecraft 中的流体类型，用于寻路系统中的流体判断
- 类型: 枚举类
- 所属模块: bukkit-navigation

## 类结构
### 公开静态字段
> EMPTY: Fluid -> 表示无流体
> WATER: Fluid -> 表示静态水
> FLOWING_WATER: Fluid -> 表示流动的水
> LAVA: Fluid -> 表示静态岩浆
> FLOWING_LAVA: Fluid -> 表示流动的岩浆

### 公开静态方法
> Block.getFluid(): Fluid -> 扩展函数，获取方块中的流体类型
> String.getFluid(): Fluid -> 扩展函数，根据方块类型名称获取对应的流体类型

### 类内可被访问字段
> 无

### 类方法
> isLava(): Boolean -> 判断当前流体是否为岩浆（包括静态和流动）
> isWater(): Boolean -> 判断当前流体是否为水（包括静态和流动）

## 实现细节
- 使用 Kotlin 枚举类定义五种基本流体状态
- 提供简便的判断方法区分水和岩浆
- 通过扩展函数简化从 Block 对象或方块类型名称获取流体类型的操作
- 兼容不同版本的 Minecraft 方块命名（如 STATIONARY_LAVA 和 LAVA）

## 使用场景
> 在寻路系统中判断实体是否可以穿过或在流体上移动
> 在 AI 行为决策中考虑流体因素
> 在路径生成时为不同流体类型分配不同的通行代价
> 在实体属性中判断是否可以在特定流体中生存或移动

## 注意事项
> 方块类型名称的匹配基于字符串比较，可能需要根据不同版本的 Minecraft 进行调整
> 某些特殊流体（如蜂蜜）未包含在枚举中，默认会被识别为 EMPTY
> 在使用 Block.getFluid() 扩展函数时，确保方块对象不为 null
