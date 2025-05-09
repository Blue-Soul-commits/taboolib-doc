# GlowManager

## 基本信息
- 类名和包路径: top.maplex.arim.tools.glow.internal.manager.GlowManager
- 基本用途: 发光效果系统的核心管理类，负责实体和方块发光效果的创建、修改和移除
- 类型: 具体类
- 所属模块: 发光效果工具模块 - 内部管理器

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> glowingEntities: ConcurrentHashMap<Player, ConcurrentHashMap<Int, GlowingEntityData>> -> 存储发光实体数据的映射表
> teams: ConcurrentHashMap<Player, ConcurrentHashMap<NamedTextColor, CopyOnWriteArraySet<String>>> -> 存储玩家团队数据的映射表
> invisibleFlag: Byte -> 实体隐形标志位(2^5 = 32)
> glowingFlag: Byte -> 实体发光标志位(2^6 = 64)
> glowingBlocks: ConcurrentHashMap<Player, ConcurrentHashMap<Block, GlowingBlockData>> -> 存储发光方块数据的映射表

### 类方法
> setEntityGlowing(entity: Entity, receiver: Player, color: NamedTextColor): Unit -> 设置实体发光效果
> unsetEntityGlowing(entity: Entity, receiver: Player): Unit -> 移除实体发光效果
> setBlockGlowing(block: Block, receiver: Player, color: NamedTextColor, mode: BlockGlowMode): Unit -> 设置方块发光效果
> unsetBlockGlowing(block: Block, receiver: Player): Unit -> 移除方块发光效果
> 私有方法：
> setEntityGlowing0(entityID: Int, teamID: String, receiver: Player, color: NamedTextColor?, otherSharedFlags: Byte): Unit -> 内部实现发光效果的核心方法
> Player.createGlowing(entityID: Int): Unit -> 扩展方法，创建发光效果
> Player.destroyGlowing(entityID: Int): Unit -> 扩展方法，移除发光效果
> Player.setGlowingColor(entityID: Int): Unit -> 扩展方法，设置发光颜色
> Player.unsetGlowingColor(entityID: Int): Unit -> 扩展方法，取消发光颜色
> Player.createDummyFallingBlock(location: Location): Pair<Int, String>? -> 扩展方法，创建虚拟掉落方块

## 实现细节
- 使用线程安全的ConcurrentHashMap和CopyOnWriteArraySet存储数据，支持并发访问
- 为每个观察者(Player)单独维护发光实体和方块的状态，实现玩家独立的视觉效果
- 提供两种方块发光模式：
  1. CLASSIC_11200_11605_UNIVERSAL: 使用潜影贝实体，保留方块交互性但形状为立方体
  2. STYLE_11200_11605_ONLY: 使用掉落方块实体，形状贴合但禁用交互，仅适用于特定版本
- 使用Minecraft团队系统(Teams)实现发光颜色的控制
- 通过实体元数据包修改实体标志位来实现发光效果的显示和隐藏
- 注册事件监听器处理玩家退出、死亡和方块破坏事件，确保正确清理发光效果数据
- 实现了颜色变更、实体移除等各种状态变化的处理逻辑
- 通过位运算操作实体的标志位，启用或禁用发光和隐形效果

## 使用场景
> 通过IGlow API被外部模块调用，为实体和方块添加发光效果
> 在游戏中为特定玩家提供视觉指引和高亮显示
> 实现玩家独立的发光效果，不影响其他玩家的视觉体验
> 根据不同需求选择合适的方块发光模式，平衡视觉效果和交互性

## 注意事项
> 这是内部类(internal.manager)，主要通过IGlow类对外提供服务
> 方块发光的STYLE模式仅支持1.12.2和1.16.5版本，其他版本需使用CLASSIC模式
> 不支持空气方块的发光效果
> 当玩家退出或死亡时，会自动清理该玩家的所有发光效果数据
> 使用方块STYLE模式时，破坏方块的事件不会被触发，因为方块交互被禁用
> 依赖PacketEvents和TabooLib库实现跨版本兼容