# BukkitEquipment

## 基本信息
- 类名和包路径: taboolib.type.BukkitEquipment
- 基本用途: 装备类型转换工具，用于统一处理不同版本 Bukkit API 中的装备操作
- 类型: 枚举类
- 所属模块: taboolib.module.bukkit.bukkit-util

## 类结构

### 公开静态字段
> HAND: BukkitEquipment -> 主手装备位置
> OFF_HAND: BukkitEquipment -> 副手装备位置
> FEET: BukkitEquipment -> 脚部装备位置
> LEGS: BukkitEquipment -> 腿部装备位置
> CHEST: BukkitEquipment -> 胸部装备位置
> HEAD: BukkitEquipment -> 头部装备位置

### 公开静态方法
> fromString(value: String): BukkitEquipment -> 通过特定名称获取装备类型
> fromNMS(nms: String): BukkitEquipment -> 通过 NMS 物品类型名称获取装备类型
> fromBukkit(bukkit: EquipmentSlot): BukkitEquipment -> 通过 Bukkit 物品类型获取装备类型
> getItems(player: Player): Map<BukkitEquipment, ItemStack> -> 获取玩家所有装备
> getItems(entity: LivingEntity): Map<BukkitEquipment, ItemStack> -> 获取实体所有装备

### 类内可被访问字段
> bukkit: EquipmentSlot -> 对应的 Bukkit EquipmentSlot 枚举值
> nms: String -> 对应的 NMS 装备名称
> slot: int -> 对应的物品栏槽位索引

### 类方法
> setItem(player: Player, item: ItemStack): void -> 为玩家设置指定位置的装备
> setItem(entity: LivingEntity, item: ItemStack): void -> 为实体设置指定位置的装备
> setItemDropChance(entity: LivingEntity, chance: float): void -> 设置实体装备掉落几率
> getItem(player: Player): ItemStack -> 获取玩家指定位置的装备
> getItem(entity: LivingEntity): ItemStack -> 获取实体指定位置的装备
> getItemDropChance(entity: LivingEntity): float -> 获取实体装备掉落几率
> getBukkit(): EquipmentSlot -> 获取对应的 Bukkit EquipmentSlot
> getNMS(): String -> 获取对应的 NMS 装备名称
> getSlot(): int -> 获取对应的物品栏槽位索引

## 实现细节
- 使用枚举类型定义了六种装备位置：主手、副手、头部、胸部、腿部和脚部
- 通过兼容性处理支持不同版本的 Bukkit API，特别是针对 OFF_HAND 位置的处理
- 使用 try-catch 块处理新旧 API 的差异，如 getItemInMainHand/getItemInHand 方法
- 提供了多种方式获取装备类型，包括字符串名称、数字索引、NMS 名称和 Bukkit 枚举
- 支持获取和设置实体装备的掉落几率
- 提供批量获取实体所有装备的方法，返回 Map 结构

## 使用场景
> 需要兼容不同版本 Bukkit API 的插件开发
> 统一处理玩家和实体的装备操作
> 通过字符串或数字索引快速引用装备位置
> 批量获取和设置实体装备
> 设置实体装备掉落几率

## 注意事项
> OFF_HAND 位置在旧版本 Minecraft 中不存在，会回退到 HAND
> 使用 @SuppressWarnings("deprecation") 注解处理已弃用的 API 方法
> 获取装备时可能返回 null，需要进行空值检查
> 槽位索引与玩家物品栏布局相关，HEAD=39, CHEST=38, LEGS=37, FEET=36, OFF_HAND=40
> 主手位置的槽位索引为 -1，表示需要特殊处理
