# Hopper
## 基本信息
- 类名和包路径: taboolib.module.ui.type.Hopper
- 基本用途: 提供漏斗类型容器界面的创建和管理功能
- 类型: 接口
- 所属模块: taboolib.module.ui
## 类结构
### 公开静态字段
> 无公开静态字段
### 公开静态方法
> 无公开静态方法
### 类内可被访问字段
> 继承自 Chest 接口的所有字段:
> rows: Int -> 获取容器的行数
> virtualized: Boolean -> 是否正在使用虚拟化
> virtualizedStorageContents: List? -> 虚拟化时玩家背包内容
> items: ConcurrentHashMap<Char, ItemStack> -> 物品与对应抽象字符关系
> slots: CopyOnWriteArrayList<List> -> 抽象字符布局
> handLocked: Boolean -> 是否锁定主手
> isOpened: Boolean -> 是否打开过
> title: String -> 容器标题
### 类方法
> 继承自 Chest 接口的所有方法:
> virtualize(storageContents: List? = null): Unit -> 启用虚拟化页面（将自动阻止所有点击行为）
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
> getSlots(slot: Char): List -> 获取抽象字符对应的位置
> getFirstSlot(slot: Char): Int -> 获取抽象字符对应的首个位置
> updateTitle(title: String): Unit -> 更新标题
> build(): Inventory -> 构建菜单
## 实现细节
> Hopper 接口继承自 Chest 接口，提供了创建和管理漏斗类型容器界面的功能
> 默认实现类为 HopperImpl，通过 Menu.getImplementation 获取
> 漏斗容器固定为 5 个槽位，布局为单行
> 在 HopperImpl 中重写了 build() 方法，使用 InventoryType.HOPPER 创建漏斗类型的容器
> 虽然继承了 Chest 接口的 rows() 方法，但对漏斗容器无实际影响，因为漏斗容器的大小是固定的
> 在使用 map() 方法设置布局时，只会使用第一行（slots[0]）的前 5 个字符
## 使用场景
> 创建简单的物品选择界面
> 实现小型菜单系统
> 构建需要较少槽位的功能界面
> 作为简洁的交互界面，如确认/取消选择
## 注意事项
> 漏斗容器固定为 5 个槽位，无法更改大小
> 使用 map() 方法时，只有第一行的前 5 个字符有效
> 继承自 Chest 的 rows() 方法对漏斗容器无实际影响
> 其他功能（如虚拟化、事件回调等）与 Chest 接口相同