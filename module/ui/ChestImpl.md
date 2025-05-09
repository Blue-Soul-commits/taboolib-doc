# ChestImpl

## 基本信息
- 类名和包路径: taboolib.module.ui.type.impl.ChestImpl
- 基本用途: 实现标准箱子类型的菜单界面，提供完整的UI构建和交互功能
- 类型: 类(Class)
- 所属模块: bukkit-ui

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> lastInventory: Inventory -> 最后一次构建的页面
> rows: Int -> 行数(1-6)
> virtualized: Boolean -> 是否启用虚拟化
> virtualizedStorageContents: List<ItemStack>? -> 虚拟化时玩家背包内容
> items: ConcurrentHashMap<Char, ItemStack> -> 物品与对应抽象字符关系
> slots: CopyOnWriteArrayList<List<Char>> -> 抽象字符布局
> handLocked: Boolean -> 是否锁定主手
> isOpened: Boolean -> 是否已打开
> holderCallback: ((menu: ChestImpl) -> MenuHolder) -> MenuHolder回调
> clickCallback: CopyOnWriteArrayList<(event: ClickEvent) -> Unit> -> 点击回调列表
> selfClickCallback: (event: ClickEvent) -> Unit -> 自定义点击回调
> closeCallback: ((event: InventoryCloseEvent) -> Unit) -> 关闭回调
> onceCloseCallback: Boolean -> 是否只触发一次关闭回调
> isSkipCloseCallbackOnUpdateTitle: Boolean -> 是否忽略updateTitle的关闭回调
> isUpdateTitle: Boolean -> 是否正在刷新标题
> buildCallback: ((player: Player, inventory: Inventory) -> Unit) -> 构建回调
> asyncBuildCallback: ((player: Player, inventory: Inventory) -> Unit) -> 异步构建回调
> selfBuildCallback: ((player: Player, inventory: Inventory) -> Unit) -> 自定义构建回调
> selfAsyncBuildCallback: ((player: Player, inventory: Inventory) -> Unit) -> 自定义异步构建回调

### 类方法
> virtualize(storageContents: List<ItemStack>?): Unit -> 使用虚拟页面
> hidePlayerInventory(): Unit -> 隐藏玩家背包
> rows(rows: Int): Unit -> 设置行数
> handLocked(handLocked: Boolean): Unit -> 设置是否锁定玩家手部动作
> holder(func: (menu: Chest) -> MenuHolder): Unit -> 设置MenuHolder创建回调
> onBuild(async: Boolean, callback: (player: Player, inventory: Inventory) -> Unit): Unit -> 页面构建时触发回调
> selfBuild(async: Boolean, callback: (player: Player, inventory: Inventory) -> Unit): Unit -> 设置自定义构建回调
> onClose(once: Boolean, skipUpdateTitle: Boolean, callback: (event: InventoryCloseEvent) -> Unit): Unit -> 页面关闭时触发回调
> onClick(bind: Int, callback: (event: ClickEvent) -> Unit): Unit -> 特定位置点击事件回调
> onClick(bind: Char, callback: (event: ClickEvent) -> Unit): Unit -> 特定抽象字符点击事件回调
> onClick(lock: Boolean, callback: (event: ClickEvent) -> Unit): Unit -> 整页点击事件回调
> selfClick(callback: (event: ClickEvent) -> Unit): Unit -> 设置自定义点击回调
> map(vararg slots: String): Unit -> 使用抽象字符页面布局
> set(slot: Char, itemStack: ItemStack): Unit -> 根据抽象符号设置物品
> set(slot: Int, itemStack: ItemStack): Unit -> 根据位置设置物品
> set(slot: Char, callback: () -> ItemStack): Unit -> 根据抽象符号设置物品(回调方式)
> set(slot: Int, callback: () -> ItemStack): Unit -> 根据位置设置物品(回调方式)
> set(slot: Char, material: XMaterial, itemBuilder: ItemBuilder.() -> Unit): Unit -> 根据抽象符号设置物品(使用ItemBuilder)
> set(slot: Int, material: XMaterial, itemBuilder: ItemBuilder.() -> Unit): Unit -> 根据位置设置物品(使用ItemBuilder)
> set(slot: Char, itemStack: ItemStack, onClick: ClickEvent.() -> Unit): Unit -> 根据抽象符号设置物品并添加点击事件
> set(slot: Int, itemStack: ItemStack, onClick: ClickEvent.() -> Unit): Unit -> 根据位置设置物品并添加点击事件
> getSlot(slot: Int): Char -> 获取位置对应的抽象字符
> getSlots(slot: Char): List<Int> -> 获取抽象字符对应的位置列表
> getFirstSlot(slot: Char): Int -> 获取抽象字符对应的首个位置
> updateTitle(title: String): Unit -> 更新标题
> createTitle(): String -> 创建标题
> build(): Inventory -> 构建页面

## 实现细节
- 使用ConcurrentHashMap和CopyOnWriteArrayList保证线程安全
- 支持虚拟化菜单，可以隐藏玩家背包
- 使用抽象字符布局系统，方便设计界面
- 支持同步和异步构建回调
- 支持多种物品设置方式，包括直接设置、回调设置和使用ItemBuilder
- 支持动态更新标题，会重新打开菜单但保持内容
- 支持锁定玩家手部动作，防止物品被拿出
- 点击事件处理会过滤拖拽类型，只处理点击类型

## 使用场景
> 创建标准的箱子类型界面，如商店、设置菜单等
> 需要使用抽象字符布局的复杂界面
> 需要动态更新内容或标题的界面
> 需要精确控制点击行为的界面
> 需要虚拟化界面以实现特殊效果的场景

## 注意事项
> 页面打开后无法设置构建回调和预设物品
> 更新标题会重新打开菜单，可能导致闪烁
> 虚拟化菜单中，player.closeInventory()不会触发关闭回调
> 行数超过6会导致客户端显示异常
> 抽象字符布局中每行不应超过9个字符
> 使用selfBuild和selfClick方法会覆盖之前设置的回调
