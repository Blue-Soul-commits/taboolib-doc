# BukkitEvent
## 基本信息
- 类名和包路径: taboolib.platform.util.BukkitEvent
- 基本用途: 提供对Bukkit事件的扩展函数，简化事件处理和判断
- 类型: Kotlin扩展函数集合
- 所属模块: bukkit-util

## 类结构
### 公开静态字段
> EntityDamageByEntityEvent.attacker: LivingEntity? -> 获取实体伤害事件中的攻击者，支持直接攻击、弹射物和唤魔者尖牙
> EntityDeathEvent.killer: LivingEntity? -> 获取实体死亡事件中的杀手，包括直接杀手或最后一次伤害的攻击者
> PlayerDeathEvent.killer: LivingEntity? -> 获取玩家死亡事件中的杀手，包括直接杀手或最后一次伤害的攻击者

### 公开静态方法
> PlayerInteractEvent.isRightClick(): Boolean -> 检查是否为右键点击（空气或方块）
> PlayerInteractEvent.isRightClickAir(): Boolean -> 检查是否为右键点击空气
> PlayerInteractEvent.isRightClickBlock(): Boolean -> 检查是否为右键点击方块
> PlayerInteractEvent.isLeftClick(): Boolean -> 检查是否为左键点击（空气或方块）
> PlayerInteractEvent.isLeftClickAir(): Boolean -> 检查是否为左键点击空气
> PlayerInteractEvent.isLeftClickBlock(): Boolean -> 检查是否为左键点击方块
> PlayerInteractEvent.isPhysical(): Boolean -> 检查是否为物理交互（如踩压力板）
> PlayerInteractEvent.isMainhand(): Boolean -> 检查是否使用主手进行交互
> PlayerInteractEvent.isOffhand(): Boolean -> 检查是否使用副手进行交互
> PlayerInteractEntityEvent.isMainhand(): Boolean -> 检查是否使用主手进行实体交互
> PlayerInteractEntityEvent.isOffhand(): Boolean -> 检查是否使用副手进行实体交互
> PlayerMoveEvent.isMovement(): Boolean -> 检查是否发生了水平移动
> PlayerMoveEvent.isBlockMovement(): Boolean -> 检查是否发生了整数坐标的水平移动
> PlayerMoveEvent.isVerticalMovement(): Boolean -> 检查是否发生了垂直移动
> PlayerMoveEvent.moveDirection(): List<MoveDirection> -> 获取玩家移动的方向列表

## 实现细节
- 使用Kotlin扩展函数为Bukkit事件类添加额外的功能，无需修改原始类
- moveDirection()方法使用向量数学计算玩家的移动方向，考虑了玩家的朝向和移动向量
- attacker属性通过类型检查和转换处理不同类型的攻击者，包括直接攻击、弹射物和特殊实体
- killer属性首先检查直接杀手，如果没有则尝试从最后一次伤害事件中获取攻击者

## 使用场景
> 简化事件处理逻辑，使代码更加清晰和简洁
> 统一处理不同类型的交互事件，如右键点击、左键点击等
> 分析玩家移动方向，用于自定义移动控制或动作检测
> 追踪实体伤害和死亡的来源，用于自定义伤害系统或统计

## 注意事项
> PlayerMoveEvent.to可能为null，但相关方法已做空值检查
> moveDirection()方法使用阈值(0.1)来判断移动方向，可能在极小移动时不够精确
> attacker和killer属性可能返回null，使用时应进行空值检查
> 在高频触发的事件(如PlayerMoveEvent)中使用复杂计算可能影响性能

