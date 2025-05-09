# VirtualClickType

## 基本信息
- 类名和包路径: taboolib.module.ui.virtual.VirtualClickType
- 基本用途: 表示虚拟界面中的点击类型，与Bukkit的ClickType对应
- 类型: 枚举类
- 所属模块: bukkit-ui

## 类结构

### 公开静态字段
> LEFT: VirtualClickType -> 左键点击
> SHIFT_LEFT: VirtualClickType -> Shift+左键点击
> RIGHT: VirtualClickType -> 右键点击
> SHIFT_RIGHT: VirtualClickType -> Shift+右键点击
> WINDOW_BORDER_LEFT: VirtualClickType -> 左键点击窗口边框
> WINDOW_BORDER_RIGHT: VirtualClickType -> 右键点击窗口边框
> MIDDLE: VirtualClickType -> 中键点击
> NUMBER_KEY: VirtualClickType -> 数字键点击
> DOUBLE_CLICK: VirtualClickType -> 双击
> DROP: VirtualClickType -> 丢弃物品
> CONTROL_DROP: VirtualClickType -> Ctrl+丢弃物品
> CREATIVE: VirtualClickType -> 创造模式点击
> SWAP_OFFHAND: VirtualClickType -> 切换副手
> UNKNOWN: VirtualClickType -> 未知点击类型

### 公开静态方法
> 无

### 类内可被访问字段
> 无

### 类方法
> toBukkit(): ClickType -> 将VirtualClickType转换为Bukkit的ClickType

## 实现细节
- 通过枚举值的顺序与Bukkit的ClickType枚举值顺序一一对应
- toBukkit()方法使用ordinal()获取枚举值的序号，然后从ClickType.values()中获取对应位置的值

## 使用场景
> 在虚拟界面系统中处理玩家点击事件时，用于标识点击类型
> 在RemoteInventory.ClickEvent中作为clickType字段使用
> 在InventoryHandlerImpl中用于将客户端点击类型转换为服务端可识别的类型

## 注意事项
> 枚举值的顺序必须与Bukkit的ClickType枚举值顺序一致，否则toBukkit()方法会返回错误的值
> 在处理点击事件时，应当考虑UNKNOWN类型的情况

