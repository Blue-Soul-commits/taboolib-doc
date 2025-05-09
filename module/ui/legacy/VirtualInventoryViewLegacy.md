# VirtualInventoryViewLegacy

## 基本信息
- 类名和包路径: taboolib.module.ui.virtual.VirtualInventoryViewLegacy
- 基本用途: 为旧版本Minecraft提供虚拟背包视图的实现，继承自Bukkit的InventoryView
- 类型: 类（Class）
- 所属模块: bukkit-ui-legacy

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> remoteInventory: RemoteInventoryLegacy -> 持有的远程背包接口实例，提供背包数据访问

### 类方法
> getTopInventory(): Inventory -> 获取顶部背包实例，委托给remoteInventory.inventory()
> getBottomInventory(): Inventory -> 获取底部背包实例，委托给remoteInventory.bottomInventory()
> getPlayer(): HumanEntity -> 获取查看此背包的玩家实例，委托给remoteInventory.viewer()
> getType(): InventoryType -> 获取背包类型，委托给remoteInventory.inventory().type

## 实现细节
- VirtualInventoryViewLegacy是Bukkit InventoryView的具体实现，用于旧版本Minecraft
- 它通过组合方式持有一个RemoteInventoryLegacy接口实例，所有方法都委托给该实例
- 此类是TabooLib虚拟背包系统中的兼容层，确保在不同Minecraft版本中能够正常创建背包视图
- 作为InventoryView的子类，它能够被Bukkit事件系统识别并处理

## 使用场景
> 在创建虚拟背包视图时，当检测到旧版本Minecraft或VirtualInventoryView创建失败时使用
> 在RemoteInventory.createInventoryView()方法中作为备选方案
> 用于确保TabooLib的虚拟背包系统在旧版本Minecraft中正常工作

## 注意事项
> 此类是为了向后兼容而设计的，在较新的Minecraft版本中应优先使用VirtualInventoryView
> 使用此类时需要提供一个正确实现的RemoteInventoryLegacy接口实例
> 通常不需要直接实例化此类，而是通过TabooLib提供的工厂方法创建
