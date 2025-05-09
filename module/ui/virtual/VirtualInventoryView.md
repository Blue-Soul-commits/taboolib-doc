# VirtualInventoryView

## 基本信息
- 类名和包路径: taboolib.module.ui.virtual.VirtualInventoryView
- 基本用途: 虚拟背包视图，用于桥接虚拟背包与Bukkit背包视图系统
- 类型: 类
- 所属模块: bukkit-ui

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> remoteInventory: RemoteInventory -> 远程背包实例
> bottomInventory: VirtualStorageInventory -> 虚拟玩家背包实例

### 类方法
> getTopInventory(): Inventory -> 获取顶部背包（虚拟背包）
> getBottomInventory(): Inventory -> 获取底部背包（玩家背包）
> getPlayer(): HumanEntity -> 获取查看背包的玩家
> getType(): InventoryType -> 获取背包类型
> getTitle(): String -> 获取背包标题

## 实现细节
- 继承自Bukkit的InventoryView，使虚拟背包能够融入Bukkit背包系统
- 通过RemoteInventory获取虚拟背包实例和玩家信息
- 使用VirtualStorageInventory作为玩家背包的虚拟实现

## 使用场景
> 在虚拟背包系统中创建符合Bukkit标准的背包视图
> 在RemoteInventory.createInventoryView方法中被创建
> 在触发InventoryOpenEvent等事件时使用

## 注意事项
> 此类是虚拟背包系统与Bukkit背包系统的桥梁
> 在Minecraft 1.21及以上版本中，会使用VirtualInventoryViewModern替代