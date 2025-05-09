# VirtualInventoryInteractEvent

## 基本信息
- 类名和包路径: taboolib.module.ui.virtual.VirtualInventoryInteractEvent
- 基本用途: 虚拟背包交互事件，用于桥接虚拟背包点击事件与Bukkit事件系统
- 类型: 类
- 所属模块: bukkit-ui

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> clickEvent: RemoteInventory.ClickEvent -> 虚拟背包点击事件对象

### 类方法
> 无（仅继承自InventoryInteractEvent的方法）

## 实现细节
- 继承自Bukkit的InventoryInteractEvent，使虚拟背包事件能够融入Bukkit事件系统
- 包装RemoteInventory.ClickEvent，提供对原始点击事件的访问
- 通过传入InventoryView参数，确保事件能够正确关联到对应的背包视图

## 使用场景
> 在虚拟背包系统中触发Bukkit事件
> 在ClickEvent类中通过virtualEvent()方法获取虚拟点击事件
> 在RemoteInventory.inject方法中创建并触发此事件

## 注意事项
> 此事件是虚拟背包系统与Bukkit事件系统的桥梁，确保插件能够监听虚拟背包的交互
> 使用此事件时需要注意区分普通背包事件和虚拟背包事件
