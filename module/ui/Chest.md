# Chest
## 基本信息
- 类名和包路径: taboolib.module.ui.type.Chest
- 基本用途: 提供标准容器界面的创建和管理功能
- 类型: 接口
- 所属模块: taboolib.module.ui

## 类结构
### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> rows: Int -> 获取容器的行数
> virtualized: Boolean -> 是否正在使用虚拟化
> virtualizedStorageContents: List<ItemStack>? -> 虚拟化时玩家背包内容
> items: ConcurrentHashMap<Char, ItemStack> -> 物品与对应抽象字符关系
> slots: CopyOnWriteArrayList<List<Char>> -> 抽象字符布局
> handLocked: Boolean -> 是否锁定主手
> isOpened: Boolean -> 是否打开过
> title: String -> 容器标题

### 类方法
> virtualize(storageContents: List<ItemStack>? = null): Unit -> 启用虚拟化页面（将自动阻止所有点击行为）
> hidePlayerInventory(): Unit -> 隐藏玩家背包（自动启动虚拟页面）
> rows(rows: Int): Unit -> 设置容器行数（1-6之间的整数）
> handLocked(handLocked: Boolean): Unit -> 设置是否锁定玩家手部动作
> holder(func: (menu: Chest) -> MenuHolder): Unit -> 设置 MenuHolder 创建回调
> onBuild(async: Boolean = false, callback: (player: Player, inventory: Inventory) -> Unit): Unit -> 页面构建时触发回调
> onClose(once: Boolean = true, skipUpdateTitle: Boolean = true, callback: (event: InventoryCloseEvent) -> Unit): Unit -> 页面关闭时触发回调
> onClick(bind: Int, callback: (event: ClickEvent) -> Unit = {}): Unit -> 点击事件回调（特定位置）
> onClick(bind: Char, callback: (event: ClickEvent) -> Unit = {}): Unit -> 点击事件回调（特定抽象字符）
> onClick(lock: Boolean = false, callback: (event: ClickEvent) -> Unit = {}): Unit -> 整页点击事件回调
> map(vararg slots: String): Unit -> 使用抽象字符页面布局
> set(slot: Char, itemStack: ItemStack): Unit -> 根据抽象符号设置物品
> set(slot: Int, itemStack: ItemStack): Unit -> 根据位置设置物品
> set(slot: Char, callback: () -> ItemStack): Unit -> 根据抽象符号设置物品（通过回调）
> set(slot: Int, callback: () -> ItemStack): Unit -> 根据位置设置物品（通过回调）
> set(slot: Char, material: XMaterial, itemBuilder: ItemBuilder.() -> Unit = {}): Unit -> 根据抽象符号设置物品（使用 ItemBuilder）
> set(slot: Int, material: XMaterial, itemBuilder: ItemBuilder.() -> Unit = {}): Unit -> 根据位置设置物品（使用 ItemBuilder）
> set(slot: Char, itemStack: ItemStack, onClick: ClickEvent.() -> Unit = {}): Unit -> 根据抽象符号设置物品并添加点击事件
> set(slot: Int, itemStack: ItemStack, onClick: ClickEvent.() -> Unit = {}): Unit -> 根据位置设置物品并添加点击事件
> getSlot(slot: Int): Char -> 获取位置对应的抽象字符
> getSlots(slot: Char): List<Int> -> 获取抽象字符对应的位置
> getFirstSlot(slot: Char): Int -> 获取抽象字符对应的首个位置
> updateTitle(title: String): Unit -> 更新标题
> build(): Inventory -> 构建菜单

## 实现细节
- Chest 接口是 TabooLib UI 模块中的核心接口，提供了创建和管理标准容器界面的功能
- 默认实现类为 ChestImpl，通过 Menu.getImplementation 获取
- 支持使用抽象字符布局来设计界面，通过 map() 方法设置布局，通过 set() 方法将物品与抽象字符关联
- 支持虚拟化功能，可以隐藏玩家背包或自定义背包内容
- 提供了丰富的事件回调机制，包括构建回调、关闭回调和点击回调
- 支持动态更新标题，通过 updateTitle() 方法实现

## 使用场景
> 创建自定义的物品展示界面
> 实现交互式菜单系统
> 构建游戏内商店、设置面板等功能界面
> 作为其他高级容器接口的基础（如 PageableChest、StorableChest 等）

## 注意事项
> 行数设置范围为 1-6，对应实际容器大小为 9-54 格
> 在页面打开后无法预设物品，需要在 onBuild 回调中设置
> 虚拟化页面会自动阻止所有点击行为
> 使用 updateTitle 方法更新标题时，会重新构建页面并对所有查看者重新打开
> 若启用虚拟化菜单，player.closeInventory() 可能不会触发关闭回调函数