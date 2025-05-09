# MenuExtensions

## 基本信息
- 类名和包路径: taboolib.module.ui.MenuExtensions
- 基本用途: 提供TabooLib菜单系统的扩展函数，增强菜单相关事件的功能
- 类型: Kotlin扩展函数文件
- 所属模块: bukkit-ui

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法（以Kotlin扩展函数形式提供）

### 类内可被访问字段
> 无类内可被访问字段

### 类方法
> InventoryCloseEvent.returnItems(slots: List<Int>): Unit -> 为InventoryCloseEvent类提供的扩展函数，用于在背包关闭时将指定槽位的物品返还给玩家

## 实现细节
- MenuExtensions.kt文件包含Kotlin扩展函数，为现有类添加新功能而不修改原类
- returnItems扩展函数为InventoryCloseEvent类添加了物品返还功能
- 该函数使用forEach循环遍历提供的槽位列表，对每个槽位调用player.giveItem方法
- 内部使用了taboolib.platform.util包中的giveItem扩展函数，简化了物品给予逻辑

## 使用场景
> 在自定义菜单关闭时，需要将玩家放入特定槽位的物品返还给玩家
> 在临时交互界面关闭时，防止玩家物品丢失
> 在合成、交易等涉及物品放置的界面关闭时，确保物品安全返还

## 注意事项
> 此扩展函数依赖taboolib.platform.util.giveItem函数，确保相关依赖可用
> 函数不会检查槽位是否有效或物品是否为null，调用时应确保提供的槽位列表合法
> 物品返还使用giveItem方法，如果玩家背包已满，物品会掉落在玩家位置
> 此函数通常在InventoryCloseEvent事件处理中调用，确保在正确的时机使用

