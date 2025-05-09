# PageableChest

## 基本信息
- 类名和包路径: taboolib.module.ui.type.PageableChest
- 基本用途: 提供可翻页的容器界面功能，用于展示大量元素
- 类型: 接口(Interface)
- 所属模块: bukkit-ui

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> page: Int -> 当前页码

### 类方法
> menuLocked(lockAll: Boolean): Unit -> 设置是否锁定所有位置，默认为true
> page(page: Int): Unit -> 设置当前页码
> slots(slots: List<Int>): Unit -> 设置可用于显示元素的位置列表
> slotsBy(char: Char): Unit -> 通过抽象字符选择由map函数铺设的页面位置
> elements(elements: () -> List<T>): Unit -> 设置可用元素列表回调
> onGenerate(async: Boolean, callback: (player: Player, element: T, index: Int, slot: Int) -> ItemStack): Unit -> 设置元素对应物品生成回调
> onBuild(async: Boolean, callback: (inventory: Inventory) -> Unit): Unit -> 设置页面构建回调
> onClick(callback: (event: ClickEvent, element: T) -> Unit): Unit -> 设置元素点击回调
> setNextPage(slot: Int, roll: Boolean, callback: (page: Int, hasNextPage: Boolean) -> ItemStack): Unit -> 设置下一页按钮
> setPreviousPage(slot: Int, roll: Boolean, callback: (page: Int, hasPreviousPage: Boolean) -> ItemStack): Unit -> 设置上一页按钮
> onPageChange(callback: (player: Player) -> Unit): Unit -> 设置切换页面回调
> hasPreviousPage(): Boolean -> 判断是否可以返回上一页
> hasNextPage(): Boolean -> 判断是否可以前往下一页
> resetElementsCache(): Unit -> 重置元素列表缓存

## 实现细节
- 继承自Chest接口，提供基础容器功能
- 通过泛型T支持任意类型的元素列表
- 实现类PageableChestImpl提供了完整的翻页逻辑
- 支持异步生成元素对应的物品，提高性能
- 支持循环翻页功能，当到达最后一页时可以回到第一页

## 使用场景
> 展示大量物品，如商店、仓库等界面
> 需要分页展示数据的任何场景，如玩家列表、任务列表等
> 需要动态更新内容的界面，如排行榜等

## 注意事项
> 使用前需要设置可用位置(slots)和元素列表(elements)
> 翻页按钮需要手动设置，不会自动添加
> 元素生成回调可能会被频繁调用，应避免在回调中执行耗时操作
> 如果元素列表发生变化，需要调用resetElementsCache()重置缓存