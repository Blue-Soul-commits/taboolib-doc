# Anvil
## 基本信息
- 类名和包路径: taboolib.module.ui.type.Anvil
- 基本用途: 提供铁砧类型的物品重命名界面
- 类型: 接口
- 所属模块: module-ui

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> 无

### 类方法
> onRename(callback: (Player, String, Inventory) -> Unit): Unit -> 设置物品被重命名时的回调函数

## 实现细节
- Anvil 接口继承自 Chest 接口，因此拥有 Chest 接口的所有功能
- 实现类 AnvilImpl 继承自 ChestImpl，同时实现了 Anvil 和 AnvilCallback 接口
- AnvilImpl 在构建时会创建一个 InventoryType.ANVIL 类型的物品栏
- 当玩家在铁砧界面中重命名物品时，会触发 onRename 回调函数
- 铁砧界面只有一行，最多可以放置 3 个物品（输入、材料和输出）
- 通过 MenuBuilder 中的 buildMenu 和 openMenu 函数创建和打开铁砧界面
- 铁砧界面支持虚拟化，可以通过 virtualize() 方法启用

## 使用场景
> 需要玩家输入文本的场景，如物品重命名、文本输入对话框等
> 需要玩家合并物品或修复物品的场景

## 注意事项
> 铁砧界面只有一行，最多只能放置 3 个物品
> 使用 map() 函数设置布局时，只会使用第一行的前三个字符
> 重命名回调通过 AnvilCallback 接口的 invoke 方法触发

