# ClickEvent

## 基本信息
- 类名和包路径: taboolib.module.ui.ClickEvent
- 基本用途: 封装Bukkit库中的各种点击事件，提供统一的接口处理不同类型的点击交互
- 类型: 类(Class)
- 所属模块: bukkit-ui

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> bukkitEvent: InventoryInteractEvent -> 原始的Bukkit事件对象
> clickType: ClickType -> 点击类型，可以是CLICK、DRAG或VIRTUAL
> slot: Char -> 点击的抽象字符位置
> builder: Chest -> 关联的容器构建器
> clicker: Player -> 点击的玩家
> inventory: Inventory -> 被点击的物品栏
> affectItems: List<ItemStack> -> 受影响的物品列表(仅CLICK类型有效)
> isCancelled: Boolean -> 事件是否被取消
> rawSlot: Int -> 原始点击位置
> hotbarKey: Int -> 键盘按键(数字键)
> currentItem: ItemStack? -> 当前点击的物品

### 类方法
> getItem(slot: Char): ItemStack? -> 获取指定抽象字符位置的物品
> getItems(slot: Char): List<ItemStack> -> 获取所有指定抽象字符位置的物品列表
> clickEvent(): InventoryClickEvent -> 转换为点击事件(仅CLICK类型有效)
> clickEventOrNull(): InventoryClickEvent? -> 安全转换为点击事件
> dragEvent(): InventoryDragEvent -> 转换为拖拽事件(仅DRAG类型有效)
> dragEventOrNull(): InventoryDragEvent? -> 安全转换为拖拽事件
> virtualEvent(): RemoteInventory.ClickEvent -> 转换为虚拟点击事件(仅VIRTUAL类型有效)
> virtualEventOrNull(): RemoteInventory.ClickEvent? -> 安全转换为虚拟点击事件
> onClick(consumer: InventoryClickEvent.() -> Unit): ClickEvent -> 安全处理点击事件
> onDrag(consumer: InventoryDragEvent.() -> Unit): ClickEvent -> 安全处理拖拽事件
> onVirtualClick(consumer: RemoteInventory.ClickEvent.() -> Unit): ClickEvent -> 安全处理虚拟点击事件

## 实现细节
- 构造函数接收原始Bukkit事件、点击类型、抽象字符位置和容器构建器
- 提供了多种安全转换方法，避免类型转换异常
- 支持三种点击类型：普通点击(CLICK)、拖拽(DRAG)和虚拟点击(VIRTUAL)
- 对不同点击类型提供了统一的属性访问接口，如rawSlot、hotbarKey和currentItem
- 错误信息支持中英文双语显示

## 使用场景
> 在UI界面中处理玩家的点击交互
> 需要区分不同类型点击行为的场景
> 需要安全访问原始Bukkit事件对象的场景
> 在虚拟界面中处理点击事件

## 注意事项
> 不同的clickType支持不同的方法，使用不匹配的方法会抛出异常
> 安全方法(如clickEventOrNull)不会抛出异常，但可能返回null
> 修改currentItem会直接影响到界面显示
> 在处理事件时应注意检查clickType，避免类型转换错误

