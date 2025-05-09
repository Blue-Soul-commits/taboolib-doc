# XPatternType

## 基本信息
- 类名和包路径: taboolib.library.xseries.XPatternType
- 基本用途: 提供跨版本的 Minecraft 旗帜图案类型支持
- 类型: 最终类，继承自 XModule<XPatternType, PatternType>
- 所属模块: TabooLib XSeries 库

## 类结构

### 公开静态字段
> REGISTRY: XRegistry<XPatternType, PatternType> -> 旗帜图案类型的注册表，用于管理 XPatternType 和 Bukkit PatternType 之间的映射
> BASE: XPatternType -> 基础图案类型
> SQUARE_BOTTOM_LEFT, SQUARE_BOTTOM_RIGHT, SQUARE_TOP_LEFT, SQUARE_TOP_RIGHT: XPatternType -> 方块图案类型
> STRIPE_BOTTOM, STRIPE_TOP, STRIPE_LEFT, STRIPE_RIGHT, STRIPE_CENTER, STRIPE_MIDDLE, STRIPE_DOWNRIGHT, STRIPE_DOWNLEFT: XPatternType -> 条纹图案类型
> SMALL_STRIPES: XPatternType -> 小条纹图案类型
> CROSS, STRAIGHT_CROSS: XPatternType -> 十字图案类型
> TRIANGLE_BOTTOM, TRIANGLE_TOP, TRIANGLES_BOTTOM, TRIANGLES_TOP: XPatternType -> 三角形图案类型
> DIAGONAL_LEFT, DIAGONAL_UP_RIGHT, DIAGONAL_UP_LEFT, DIAGONAL_RIGHT: XPatternType -> 对角线图案类型
> CIRCLE, RHOMBUS: XPatternType -> 圆形和菱形图案类型
> HALF_VERTICAL, HALF_HORIZONTAL, HALF_VERTICAL_RIGHT, HALF_HORIZONTAL_BOTTOM: XPatternType -> 半分图案类型
> BORDER, CURLY_BORDER: XPatternType -> 边框图案类型
> CREEPER, SKULL, FLOWER, MOJANG, GLOBE, PIGLIN, FLOW, GUSTER: XPatternType -> 特殊图案类型
> GRADIENT, GRADIENT_UP, BRICKS: XPatternType -> 渐变和砖块图案类型

### 公开静态方法
> of(patternType: PatternType): XPatternType -> 根据 Bukkit PatternType 获取对应的 XPatternType
> of(patternType: String): Optional<XPatternType> -> 根据图案类型名称获取对应的 XPatternType
> getValues(): Collection<XPatternType> -> 获取所有可用的 XPatternType 值的不可修改集合

### 类内可被访问字段
> 无特定字段（继承自 XModule 的字段）

### 类方法
> friendlyName(): String -> 返回友好可读的图案类型名称
> isSupported(): boolean -> 检查当前服务器版本是否支持该图案类型
> or(other: XPatternType): XPatternType -> 如果当前图案类型不受支持，则返回替代图案类型

## 实现细节
- 继承自 XModule 类，提供了跨版本兼容性支持
- 使用 XRegistry 系统管理旗帜图案类型的映射关系
- 通过 std() 方法注册标准图案类型，支持多个名称映射到同一图案类型
- 部分图案类型包含版本注释，指示在不同 Minecraft 版本中的名称变化（如 1.19.4）

## 使用场景
> 在不同 Minecraft 版本间创建一致的旗帜图案
> 在插件中处理旗帜相关功能时提供向后兼容性
> 通过名称或 Bukkit PatternType 查找对应的 XPatternType

## 注意事项
> 某些图案类型在特定版本中可能有不同的名称，使用前应检查 isSupported() 方法
> 使用 of() 方法获取 XPatternType 实例，而不是直接使用静态字段，以确保跨版本兼容性
> 当处理用户输入的图案类型名称时，应使用 of(String) 方法进行安全转换

