# VirtualInventoryViewModern

## 基本信息
- 类名和包路径: taboolib.module.ui.virtual.VirtualInventoryViewModern
- 基本用途: 为现代版本Minecraft（1.21+）提供虚拟背包视图的实现，继承自CraftAbstractInventoryView
- 类型: 类（Class）
- 所属模块: bukkit-ui-12100

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> newInstance(remoteInventory: RemoteInventoryModern): InventoryView -> 创建VirtualInventoryViewModern实例的工厂方法

### 类内可被访问字段
> remoteInventory: RemoteInventoryModern -> 持有的远程背包接口实例，提供背包数据访问

### 类方法
> getTopInventory(): Inventory -> 获取顶部背包实例，委托给remoteInventory.inventory()
> getBottomInventory(): Inventory -> 获取底部背包实例，委托给remoteInventory.bottomInventory()
> getPlayer(): HumanEntity -> 获取查看此背包的玩家实例，委托给remoteInventory.viewer()
> getType(): InventoryType -> 获取背包类型，委托给remoteInventory.inventory().type
> getTitle(): String -> 获取背包标题，委托给remoteInventory.title()
> getOriginalTitle(): String -> 获取原始背包标题，委托给remoteInventory.title()
> setTitle(p0: String): void -> 设置背包标题的空实现方法

## 实现细节
- VirtualInventoryViewModern继承自CraftAbstractInventoryView，适用于Minecraft 1.21及以上版本
- 它通过组合方式持有一个RemoteInventoryModern接口实例，所有方法都委托给该实例
- 相比VirtualInventoryViewLegacy，它增加了标题相关的方法实现（getTitle、getOriginalTitle、setTitle）
- 提供了一个静态工厂方法newInstance，简化创建实例的过程
- setTitle方法是一个空实现，表明不支持动态修改背包标题

## 使用场景
> 在创建虚拟背包视图时，当检测到现代版本Minecraft（1.21+）时使用
> 在RemoteInventory.createInventoryView()方法中，当检测到高版本时优先使用
> 用于确保TabooLib的虚拟背包系统在最新Minecraft版本中正常工作，支持标题功能

## 注意事项
> 此类专为Minecraft 1.21及以上版本设计，在较旧版本中应使用VirtualInventoryViewLegacy
> 使用此类时需要提供一个正确实现的RemoteInventoryModern接口实例
> 通常应通过companion object中的newInstance工厂方法创建实例，而非直接使用构造函数
> setTitle方法为空实现，意味着一旦创建，背包标题无法被修改
