# XAttribute

## 基本信息
- 类名和包路径: taboolib.library.xseries.XAttribute
- 基本用途: 提供跨版本兼容的 Minecraft 属性系统封装，用于处理游戏中的各种属性（如生命值、攻击力等）
- 类型: 最终类（final class）
- 所属模块: TabooLib platform-bukkit-impl

## 类结构

### 公开静态字段
> REGISTRY: XRegistry<XAttribute, Attribute> -> 属性注册表，用于管理所有 XAttribute 实例
> MAX_HEALTH: XAttribute -> 最大生命值属性
> FOLLOW_RANGE: XAttribute -> 跟随范围属性
> KNOCKBACK_RESISTANCE: XAttribute -> 击退抗性属性
> MOVEMENT_SPEED: XAttribute -> 移动速度属性
> FLYING_SPEED: XAttribute -> 飞行速度属性
> ATTACK_DAMAGE: XAttribute -> 攻击伤害属性
> ATTACK_KNOCKBACK: XAttribute -> 攻击击退属性
> ATTACK_SPEED: XAttribute -> 攻击速度属性
> ARMOR: XAttribute -> 护甲属性
> ARMOR_TOUGHNESS: XAttribute -> 护甲韧性属性
> FALL_DAMAGE_MULTIPLIER: XAttribute -> 摔落伤害倍率属性
> LUCK: XAttribute -> 幸运属性
> MAX_ABSORPTION: XAttribute -> 最大伤害吸收属性
> SAFE_FALL_DISTANCE: XAttribute -> 安全摔落距离属性
> SCALE: XAttribute -> 缩放属性
> STEP_HEIGHT: XAttribute -> 步高属性
> GRAVITY: XAttribute -> 重力属性
> JUMP_STRENGTH: XAttribute -> 跳跃强度属性
> BURNING_TIME: XAttribute -> 燃烧时间属性
> EXPLOSION_KNOCKBACK_RESISTANCE: XAttribute -> 爆炸击退抗性属性
> MOVEMENT_EFFICIENCY: XAttribute -> 移动效率属性
> OXYGEN_BONUS: XAttribute -> 氧气奖励属性
> WATER_MOVEMENT_EFFICIENCY: XAttribute -> 水中移动效率属性
> TEMPT_RANGE: XAttribute -> 诱惑范围属性
> BLOCK_INTERACTION_RANGE: XAttribute -> 方块交互范围属性
> ENTITY_INTERACTION_RANGE: XAttribute -> 实体交互范围属性
> BLOCK_BREAK_SPEED: XAttribute -> 方块破坏速度属性
> MINING_EFFICIENCY: XAttribute -> 挖掘效率属性
> SNEAKING_SPEED: XAttribute -> 潜行速度属性
> SUBMERGED_MINING_SPEED: XAttribute -> 水下挖掘速度属性
> SWEEPING_DAMAGE_RATIO: XAttribute -> 横扫伤害比例属性
> SPAWN_REINFORCEMENTS: XAttribute -> 生成增援属性

### 公开静态方法
> createModifier(key: String, amount: double, operation: AttributeModifier.Operation, slot: EquipmentSlot): AttributeModifier -> 创建一个属性修饰符，根据服务器版本使用不同的构造方法
> of(attribute: Attribute): XAttribute -> 根据 Bukkit 属性获取对应的 XAttribute 实例
> of(attribute: String): Optional<XAttribute> -> 根据属性名称获取对应的 XAttribute 实例
> values(): XAttribute[] -> 获取所有 XAttribute 实例数组（已弃用）
> getValues(): Collection<XAttribute> -> 获取所有 XAttribute 实例集合

### 类内可被访问字段
> SUPPORTS_MODERN_MODIFIERS: boolean -> 标记是否支持现代属性修饰符（1.20.3+）

### 类方法
> XAttribute(attribute: Attribute, names: String[]) -> 私有构造方法，用于创建 XAttribute 实例

## 实现细节
- 使用 XRegistry 管理所有属性实例，提供跨版本兼容性
- 通过静态初始化块检测服务器是否支持现代属性修饰符（1.20.3+）
- 使用命名空间键（NamespacedKey）或 UUID 创建属性修饰符，取决于服务器版本
- 支持多种命名格式，包括 1.20.3+ 的新命名和旧版本的命名

## 使用场景
> 创建具有特定属性的物品，如增加攻击力、移动速度等
> 获取实体的属性值，如最大生命值、攻击伤害等
> 修改实体的属性，如增加或减少移动速度、攻击力等
> 跨版本兼容处理，确保插件在不同版本的 Minecraft 服务器上正常工作

## 注意事项
> 属性名称在不同 Minecraft 版本中可能不同，特别是 1.20.3+ 版本引入了新的命名格式
> 创建属性修饰符时需要考虑服务器版本兼容性
> 某些属性可能在特定版本中不可用，使用前应检查是否支持
> 使用已弃用的 values() 方法会导致警告，应使用 getValues() 替代
