# InventoryViewInterface

## 基本信息
- 类名和包路径: taboolib.module.ui.util.InventoryViewInterface
- 基本用途: 提供对Bukkit InventoryView接口的统一访问方法，作为跨版本兼容层
- 类型: 单例对象（Object）
- 所属模块: bukkit-ui-12100

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> getTopInventory(view: InventoryView): Inventory -> 获取视图的顶部背包
> getBottomInventory(view: InventoryView): Inventory -> 获取视图的底部背包
> getCursor(view: InventoryView): ItemStack? -> 获取视图中光标上的物品
> setCursor(view: InventoryView, item: ItemStack?) -> 设置视图中光标上的物品
> getInventory(view: InventoryView, slot: Int): Inventory? -> 根据槽位获取对应的背包实例
> getSlotType(view: InventoryView, slot: Int): SlotType -> 获取指定槽位的类型
> getTitle(view: InventoryView): String -> 获取视图的标题

### 类内可被访问字段
> 无类内可被访问字段

### 类方法
> 所有方法都是静态方法，见公开静态方法部分

## 实现细节
- InventoryViewInterface是一个工具类，以单例对象（Kotlin object）的形式实现
- 它封装了对Bukkit InventoryView接口的所有常用操作，提供统一的访问方式
- 所有方法都是简单的委托调用，将请求转发给实际的InventoryView实例
- 代码中注释掉了两个方法（getOpenInventory和getView），标注为"此方法不生效"

## 使用场景
> 在需要跨版本兼容的插件中，统一访问InventoryView的属性和方法
> 在TabooLib的虚拟背包系统中，作为与Bukkit背包API交互的桥梁
> 在处理背包事件时，提供一致的方式获取和操作背包视图的各个部分

## 注意事项
> 此类是一个纯工具类，不维护任何状态，所有方法都是无状态的
> 注释掉的方法（getOpenInventory和getView）被标记为不生效，使用时应避免尝试使用这些方法
> 作为兼容层，此类的存在是为了解决不同Minecraft版本之间API差异的问题
> 在使用时应确保传入的InventoryView实例是有效的，否则可能导致空指针异常
