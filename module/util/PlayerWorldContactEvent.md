# PlayerWorldContactEvent

## 基本信息
- 类名和包路径: taboolib.platform.event.PlayerWorldContactEvent
- 基本用途: 将玩家的各种交互行为（左键、右键、物理交互等）统一成单个事件，方便处理
- 类型: 事件类
- 所属模块: taboolib.module.bukkit.bukkit-util

## 类结构

### 公开静态字段
> usePriority: EventPriority -> 事件监听的优先级，默认为NORMAL
> ignoreCancelled: Boolean -> 是否忽略已取消的事件，默认为true
> isListened: Boolean -> 本插件是否监听了PlayerWorldContactEvent事件

### 公开静态方法
> 无

### 类内可被访问字段
> player: Player -> 交互的玩家
> action: Action -> 交互的动作
> isLeftClick: Boolean -> 是否为左键点击（包括左键方块和左键实体）
> isLeftClickAir: Boolean -> 是否为左键点击空气
> isLeftClickNotAir: Boolean -> 是否为左键点击非空气
> isLeftClickBlock: Boolean -> 是否为左键点击方块
> isRightClick: Boolean -> 是否为右键点击（包括右键方块和右键实体）
> isRightClickAir: Boolean -> 是否为右键点击空气
> isRightClickNotAir: Boolean -> 是否为右键点击非空气
> isRightClickBlock: Boolean -> 是否为右键点击方块
> isLeftClickEntity: Boolean -> 是否为左键点击实体
> isRightClickEntity: Boolean -> 是否为右键点击实体
> isPhysical: Boolean -> 是否为物理交互（如踩压力板）
> isMainHand: Boolean -> 是否使用主手
> isOffHand: Boolean -> 是否使用副手

### 类方法
> onEnable(): void -> 在插件启用时注册各种事件监听器

## 实现细节
- 继承自CancelableInternalEvent，支持取消事件
- 使用密封类Action表示不同类型的交互动作，包括：
  - LeftClickBlock: 左键点击方块
  - RightClickBlock: 右键点击方块
  - LeftClickEntity: 左键点击实体
  - RightClickEntity: 右键点击实体
  - Physical: 物理交互（如踩压力板）
- 通过监听原版事件并转换为统一的PlayerWorldContactEvent：
  - EntityDamageByEntityEvent -> LeftClickEntity
  - PlayerInteractEvent -> LeftClickBlock/RightClickBlock/Physical
  - PlayerInteractAtEntityEvent -> RightClickEntity
- 提供多种便捷属性判断交互类型，如isLeftClick、isRightClickAir等
- 使用@Inject和@PlatformSide注解标记只在Bukkit平台注入
- 使用@Awake(LifeCycle.ENABLE)在插件启用时自动注册事件监听器
- 只有当有其他插件监听了PlayerWorldContactEvent时才会注册原版事件监听器

## 使用场景
> 统一处理玩家的各种交互行为
> 简化交互事件的监听和处理逻辑
> 实现自定义交互机制，如特殊物品的使用效果
> 拦截和修改玩家的交互行为
> 创建交互式GUI或游戏机制

## 注意事项
> 事件可以被取消，取消后会同时取消原始的交互事件
> 默认使用NORMAL优先级监听原版事件，可以通过修改usePriority属性调整
> 默认忽略已取消的事件，可以通过修改ignoreCancelled属性调整
> 只有当有其他插件监听了PlayerWorldContactEvent时才会注册原版事件监听器
> 物理交互（如踩压力板）的hand属性固定为FEET
