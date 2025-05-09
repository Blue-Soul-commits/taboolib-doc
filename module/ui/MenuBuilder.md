# MenuBuilder

## 基本信息
- 类名和包路径: taboolib.module.ui.MenuBuilder
- 基本用途: 提供菜单构建和操作的核心功能，包括原始标题支持、菜单构建和打开方法
- 类型: Kotlin文件(包含顶层函数和变量)
- 所属模块: bukkit-ui

## 类结构

### 公开静态字段
> isRawTitleInVanillaInventoryEnabled: Boolean -> 是否启用了在原版物品栏中使用Raw Title的功能(只读)

### 公开静态方法
> enableRawTitleInVanillaInventory(): Unit -> 启用在原版物品栏中使用Raw Title的功能
> buildMenu<T : Menu>(title: String, builder: T.() -> Unit): Inventory -> 构建一个指定类型的菜单
> HumanEntity.openMenu<T : Menu>(title: String, builder: T.() -> Unit): Unit -> 为实体构建并打开一个菜单
> HumanEntity.openMenu(buildMenu: Inventory, changeId: Boolean): Unit -> 为实体打开一个已构建的菜单
> InventoryClickEvent.getAffectItems(): List<ItemStack> -> 获取点击事件中所有受影响的物品

### 类内可被访问字段
> 无类内可被访问字段(文件级别)

### 类方法
> 无类方法(文件级别)

## 实现细节
- 使用内联函数和泛型实现菜单构建，支持DSL风格的API
- 通过反射获取菜单实现类，支持接口到实现类的自动映射
- 支持虚拟菜单和普通菜单的统一处理
- 通过数据包拦截实现Raw Title功能，支持JSON格式的标题
- 使用InternalEventBus进行插件间通信，通知Raw Title功能的启用

## 使用场景
> 创建和打开各种类型的菜单界面
> 需要使用JSON格式标题(如颜色、悬浮文本等)的场景
> 需要虚拟化菜单以提供更高级功能的场景
> 处理物品栏点击事件，获取受影响的物品

## 注意事项
> Raw Title功能需要手动启用，默认不启用以避免不必要的性能损耗
> 虚拟菜单不需要开启Raw Title功能，它们本身就支持
> 菜单构建过程中的异常会被捕获并打印，但不会向上传播
> 使用泛型参数T必须是Menu接口或其子类型

