# StorableChest

## 基本信息
- 类名和包路径: taboolib.module.ui.type.StorableChest
- 基本用途: 提供可存储物品的容器界面功能，允许玩家放入和取出物品
- 类型: 接口(Interface)
- 所属模块: bukkit-ui

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> 无直接可被访问字段

### 类方法
> rule(rule: Rule.() -> Unit): Unit -> 定义页面规则，通过DSL方式配置容器的行为

## 内部接口: Rule

### 类方法
> checkSlot(intRange: Int, checkSlot: (inventory: Inventory, itemStack: ItemStack) -> Boolean): Unit -> 定义单个位置的物品放入判定规则
> checkSlot(intRange: IntRange, callback: (inventory: Inventory, itemStack: ItemStack) -> Boolean): Unit -> 定义一个范围内位置的物品放入判定规则
> checkSlot(callback: (inventory: Inventory, itemStack: ItemStack, slot: Int) -> Boolean): Unit -> 定义全局的物品放入判定规则
> firstSlot(firstSlot: (inventory: Inventory, itemStack: ItemStack) -> Int): Unit -> 定义获取首个有效位置的规则，用于Shift点击快速放入物品
> writeItem(writeItem: (inventory: Inventory, itemStack: ItemStack, slot: Int) -> Unit): Unit -> 定义物品写入规则
> writeItem(writeItem: (inventory: Inventory, itemStack: ItemStack, slot: Int, type: BukkitClickType) -> Unit): Unit -> 定义带点击类型的物品写入规则
> readItem(readItem: (inventory: Inventory, slot: Int) -> ItemStack?): Unit -> 定义物品读取规则

## 实现细节
- 继承自Chest接口，提供基础容器功能
- 通过Rule接口定义容器的交互规则
- 实现类StorableChestImpl提供了完整的物品存取逻辑
- 支持自定义物品存取规则，可以限制特定物品的放入
- 支持Shift点击快速放入物品的功能

## 使用场景
> 需要玩家能够存取物品的界面，如背包、仓库等
> 需要限制特定位置只能放入特定物品的界面，如合成界面
> 需要自定义物品存取逻辑的任何场景，如物品兑换、物品升级等

## 注意事项
> 在虚拟化页面中无法更改规则
> 默认情况下，所有位置都允许放入任何物品
> 如果没有定义firstSlot回调，Shift点击快速放入物品功能将不可用
> 自定义writeItem和readItem时需要注意处理越界情况
