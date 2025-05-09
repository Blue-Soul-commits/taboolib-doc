# RemoteInventoryLegacy

## 基本信息
- 类名和包路径: taboolib.module.ui.virtual.RemoteInventoryLegacy
- 基本用途: 提供虚拟背包视图的基础接口，用于在不同Minecraft版本中兼容地创建InventoryView
- 类型: 接口（Interface）
- 所属模块: bukkit-ui-legacy

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> 无类内可被访问字段

### 类方法
> inventory(): Inventory -> 获取顶部背包实例
> bottomInventory(): Inventory -> 获取底部背包实例（通常是玩家背包）
> viewer(): Player -> 获取查看此背包的玩家实例

## 实现细节
- RemoteInventoryLegacy是一个简单的接口，定义了创建虚拟背包视图所需的基本方法
- 它是TabooLib虚拟背包系统中的一个组件，用于在旧版本Minecraft中创建InventoryView
- 通过VirtualInventoryViewLegacy类实现了与Bukkit InventoryView的兼容
- 相比RemoteInventoryModern接口，它不包含title()方法，适用于较旧的Minecraft版本

## 使用场景
> 在创建虚拟背包视图时，当检测到旧版本Minecraft时使用
> 在RemoteInventory.createInventoryView()方法中，当尝试创建VirtualInventoryView失败时作为备选方案
> 作为虚拟背包系统中的兼容层，确保插件在不同Minecraft版本中正常工作

## 注意事项
> 此接口是为了向后兼容而设计的，在较新的Minecraft版本中应优先使用RemoteInventoryModern
> 实现此接口时需要确保三个方法都正确实现，以便VirtualInventoryViewLegacy能够正常工作
> 通常不需要直接实现此接口，而是通过TabooLib提供的工厂方法创建虚拟背包