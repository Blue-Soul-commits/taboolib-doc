# InventoryViewProxy

## 基本信息
- 类名和包路径: taboolib.module.ui.InventoryViewProxy
- 基本用途: 提供对Bukkit InventoryView接口的统一访问代理，解决不同Minecraft版本中InventoryView实现差异
- 类型: 单例对象（Object）
- 所属模块: bukkit-ui

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> getTopInventory(view: InventoryView): Inventory -> 获取视图的顶部背包
> getBottomInventory(view: InventoryView): Inventory -> 获取视图的底部背包
> getCursor(view: InventoryView): ItemStack? -> 获取视图中光标上的物品
> setCursor(view: InventoryView, item: ItemStack?) -> 设置视图中光标上的物品
> getInventory(view: InventoryView, slot: Int): Inventory? -> 根据槽位获取对应的背包实例
> getSlotType(view: InventoryView, slot: Int): InventoryType.SlotType -> 获取指定槽位的类型
> getTitle(view: InventoryView): String -> 获取视图的标题

### 类内可被访问字段
> isInterfaceInventoryView: Boolean -> 私有字段，通过unsafeLazy延迟初始化，用于检测当前环境中InventoryView是否为接口

### 类方法
> 所有方法都是静态方法，见公开静态方法部分

## 实现细节
- InventoryViewProxy是一个代理类，根据运行环境动态选择访问InventoryView的方式
- 使用unsafeLazy延迟初始化isInterfaceInventoryView字段，避免在类加载时就检测环境
- 每个方法都会先检查isInterfaceInventoryView，如果为true则通过InventoryViewInterface访问，否则直接访问
- 注释掉了两个扩展函数（getFixedOpenInventory和getFixedView），标注为"此方法不生效"
- 所有方法都是简单的条件判断和委托调用，不包含复杂逻辑

## 使用场景
> 在需要跨版本兼容的插件中，统一访问InventoryView的属性和方法
> 在TabooLib的虚拟背包系统中，作为与Bukkit背包API交互的桥梁
> 在处理背包事件时，提供一致的方式获取和操作背包视图的各个部分
> 解决Minecraft 1.21版本中InventoryView从类变为接口的兼容性问题

## 注意事项
> 此类是一个代理层，根据运行环境动态选择实现方式，确保在不同Minecraft版本中正常工作
> 注释掉的方法（getFixedOpenInventory和getFixedView）被标记为不生效，使用时应避免尝试使用这些方法
> isInterfaceInventoryView字段使用unsafeLazy延迟初始化，确保在实际使用时才进行环境检测
> 在使用时应确保传入的InventoryView实例是有效的，否则可能导致空指针异常
> 此类与InventoryViewInterface配合使用，共同解决Minecraft 1.21版本中API变化带来的兼容性问题

