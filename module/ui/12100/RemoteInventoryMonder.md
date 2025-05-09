# RemoteInventoryModern

## 基本信息
- 类名和包路径: taboolib.module.ui.virtual.RemoteInventoryModern
- 基本用途: 为现代版本Minecraft提供虚拟背包视图的基础接口，用于创建兼容的InventoryView
- 类型: 接口（Interface）
- 所属模块: bukkit-ui-12100

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
> title(): String -> 获取背包标题

## 实现细节
- RemoteInventoryModern是一个简单的接口，定义了创建现代版本虚拟背包视图所需的基本方法
- 它是TabooLib虚拟背包系统中的一个组件，用于在Minecraft 1.21及以上版本中创建InventoryView
- 相比RemoteInventoryLegacy接口，它增加了title()方法，适用于较新的Minecraft版本
- 通过VirtualInventoryViewModern类实现了与Bukkit InventoryView的兼容

## 使用场景
> 在创建虚拟背包视图时，当检测到现代版本Minecraft（1.21+）时使用
> 在RemoteInventory.createInventoryView()方法中，当检测到高版本时优先使用
> 作为虚拟背包系统中的兼容层，确保插件在最新Minecraft版本中正常工作

## 注意事项
> 此接口是为了现代版本Minecraft设计的，在较旧的版本中应使用RemoteInventoryLegacy
> 实现此接口时需要确保四个方法都正确实现，以便VirtualInventoryViewModern能够正常工作
> 通常不需要直接实现此接口，而是通过TabooLib提供的工厂方法创建虚拟背包
> 注意JavaDoc中的包路径注释错误，显示为"taboolib.module.ui.virtual.RemoteInventoryLegacy"，实际应为"RemoteInventoryModern"
