# AnvilImpl

## 基本信息
- 类名和包路径: taboolib.module.ui.type.impl.AnvilImpl
- 基本用途: 实现铁砧类型的菜单界面，支持物品重命名功能
- 类型: 类(Class)
- 所属模块: bukkit-ui

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> renameCallback: ((Player, String, Inventory) -> Unit)? -> 重命名回调函数

### 类方法
> onRename(callback: (Player, String, Inventory) -> Unit): Unit -> 设置物品重命名回调
> invoke(player: Player, text: String, inventory: Inventory): Unit -> 触发重命名回调
> build(): Inventory -> 构建铁砧界面

## 实现细节
- 继承自ChestImpl，复用了大部分标准箱子界面的功能
- 实现了Anvil和AnvilCallback接口，提供铁砧特有的功能
- 使用InventoryType.ANVIL创建特殊类型的物品栏
- 支持虚拟化铁砧界面
- 只使用第一行的布局，最多支持3个位置(铁砧的输入、输入和结果槽)
- 通过AnvilCallback接口的invoke方法接收玩家输入的文本

## 使用场景
> 需要玩家输入文本的场景，如创建标签、重命名物品等
> 需要模拟铁砧界面的场景
> 需要玩家通过铁砧界面进行交互的场景
> 创建自定义的铁砧工作台功能

## 注意事项
> 铁砧界面只有3个槽位，超出的布局会被忽略
> 需要正确处理renameCallback可能为null的情况
> 虚拟化铁砧界面可能在某些版本的Minecraft中有兼容性问题
> 继承了ChestImpl的所有功能，但部分功能可能不适用于铁砧界面

