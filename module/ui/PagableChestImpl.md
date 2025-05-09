# PageableChestImpl

## 基本信息
- 类名和包路径: taboolib.module.ui.type.impl.PageableChestImpl
- 基本用途: 实现可分页的物品栏界面
- 类型: 开放泛型类
- 所属模块: taboolib.module.ui

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> page: Int -> 当前页码
> maxPage: Int -> 总页数
> viewer: Player -> 查看页面的玩家
> menuLocked: Boolean -> 是否锁定所有位置
> menuSlots: CopyOnWriteArrayList<Int> -> 页面可用位置列表
> elementsCallback: () -> List<T> -> 页面可用元素回调
> elementsCache: List<T> -> 页面可用元素缓存
> elementClickCallback: (event: ClickEvent, element: T) -> Unit -> 元素点击事件回调
> generateCallback: (player: Player, element: T, index: Int, slot: Int) -> ItemStack -> 元素生成回调
> asyncGenerateCallback: (player: Player, element: T, index: Int, slot: Int) -> ItemStack -> 异步元素生成回调
> pageChangeCallback: (player: Player) -> Unit -> 页面切换回调

### 类方法
> menuLocked(lockAll: Boolean): Unit -> 设置是否锁定所有位置
> page(page: Int): Unit -> 设置页数
> slots(slots: List<Int>): Unit -> 设置可用位置
> slotsBy(char: Char): Unit -> 通过抽象字符选择页面位置
> elements(elements: () -> List<T>): Unit -> 设置可用元素列表回调
> onGenerate(async: Boolean, callback: (player: Player, element: T, index: Int, slot: Int) -> ItemStack): Unit -> 设置元素对应物品生成回调
> onBuild(async: Boolean, callback: (inventory: Inventory) -> Unit): Unit -> 设置页面构建回调
> onClick(callback: (event: ClickEvent, element: T) -> Unit): Unit -> 设置元素点击回调
> setNextPage(slot: Int, roll: Boolean, callback: (page: Int, hasNextPage: Boolean) -> ItemStack): Unit -> 设置下一页按钮
> setPreviousPage(slot: Int, roll: Boolean, callback: (page: Int, hasPreviousPage: Boolean) -> ItemStack): Unit -> 设置上一页按钮
> onPageChange(callback: (player: Player) -> Unit): Unit -> 设置页面切换回调
> hasPreviousPage(): Boolean -> 判断是否可以返回上一页
> hasNextPage(): Boolean -> 判断是否可以前往下一页
> createTitle(): String -> 创建标题，支持页码变量
> resetElementsCache(): Unit -> 重置元素列表缓存
> build(): Inventory -> 构建页面
> isNext(page: Int, size: Int, entry: Int): Boolean -> 判断是否存在下一页

## 实现细节
- 继承自ChestImpl，实现了PageableChest接口
- 使用泛型T表示页面中的元素类型，可以是任意对象
- 通过menuSlots存储可用于显示元素的位置
- 使用elementsCallback获取元素列表，elementsCache缓存元素
- 支持同步和异步生成元素对应的物品
- 支持循环翻页功能，可以从最后一页回到第一页，或从第一页回到最后一页
- 标题支持%p变量，会被替换为当前页码+1
- 计算最大页数时使用元素总数除以可用位置数量
- 使用subList获取当前页需要显示的元素子集

## 使用场景
> 需要展示大量物品时，可以分页显示
> 制作物品列表、商店、背包管理等需要分页的界面
> 需要对列表中元素进行交互操作时

## 注意事项
> 使用前需要设置menuSlots，否则无法显示任何元素
> 使用前需要设置elementsCallback，提供要显示的元素列表
> 需要设置generateCallback，将元素转换为物品显示
> 页码从0开始计算，但显示给用户时通常需要+1
> 虚拟化页面时需要特殊处理页面刷新
