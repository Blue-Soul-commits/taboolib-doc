# ItemMatcher

## 基本信息
- 类名和包路径: taboolib.platform.util.ItemMatcher
- 基本用途: 提供物品匹配、检查和操作的扩展函数
- 类型: Kotlin扩展函数集合
- 所属模块: bukkit-util

## 类结构

### 公开静态方法
> Player.checkItem(item: ItemStack, amount: Int = 1, remove: Boolean = false): Boolean -> 检查玩家背包中的特定物品是否达到特定数量
> Inventory.checkItem(item: ItemStack, amount: Int = 1, remove: Boolean = false): Boolean -> 检查背包中的特定物品是否达到特定数量
> Inventory.hasItem(amount: Int = 1, matcher: (itemStack: ItemStack) -> Boolean): Boolean -> 检查背包中符合特定规则的物品是否达到特定数量
> Inventory.takeItem(amount: Int = 1, takeList: MutableList<ItemStack> = mutableListOf(), matcher: (itemStack: ItemStack) -> Boolean): Boolean -> 移除背包中特定数量的符合特定规则的物品
> Inventory.countItem(matcher: (itemStack: ItemStack) -> Boolean): Int -> 获取背包中符合特定规则的物品的数量

## 实现细节
- 使用Kotlin扩展函数为Player和Inventory类提供额外功能
- 通过高阶函数matcher实现自定义物品匹配规则
- 支持物品数量的精确计算和操作
- 在移除物品时会保留被移除物品的副本
- 所有方法都会检查物品是否为空气，避免对空气物品进行操作

## 使用场景
> 检查玩家是否拥有足够的特定物品时
> 需要从玩家背包中移除特定物品时
> 需要统计玩家背包中特定物品数量时
> 实现自定义物品匹配逻辑时
> 开发经济、任务或交易系统时

## 注意事项
> 对空气物品进行操作会抛出"air"错误
> takeItem方法会修改原始物品栏内容
> 物品匹配使用isSimilar方法，会比较物品的类型、耐久、元数据等
> 自定义matcher可以实现更复杂的匹配逻辑
