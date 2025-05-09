# InventoryHandlerImpl

## 基本信息
- 类名和包路径: taboolib.module.ui.virtual.InventoryHandlerImpl
- 基本用途: InventoryHandler的具体实现，处理不同Minecraft版本的虚拟背包操作
- 类型: 类
- 所属模块: bukkit-ui

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> major: Int -> 当前Minecraft主版本号

### 类方法
> craftChatMessageToPlain(message: Any): String -> 将NMS聊天组件转换为纯文本
> parseToCraftChatMessage(source: String): Any -> 将字符串解析为NMS聊天组件
> openInventory(player: Player, inventory: VirtualInventory, cursorItem: ItemStack, updateId: Boolean): RemoteInventory -> 为玩家打开虚拟背包

## 实现细节
- 通过MinecraftVersion判断当前服务器版本，使用对应版本的NMS代码
- 支持从1.8到1.21的Minecraft版本
- 内部类VInventory实现了RemoteInventory接口，提供了虚拟背包的具体功能
- 使用typealias简化不同版本NMS类的引用
- 通过数据包操作实现虚拟背包的各种功能，如打开、关闭、更新物品等

## 使用场景
> 创建和管理虚拟背包界面
> 处理玩家与虚拟背包的交互，如点击、关闭等操作
> 在不同Minecraft版本中提供一致的虚拟背包体验

## 注意事项
> 由于直接使用NMS代码，每个Minecraft版本都需要特定的适配
> 使用@Suppress("CAST_NEVER_SUCCEEDS")注解标记的方法可能存在类型转换问题
> 在处理点击事件时，需要考虑不同版本的数据包结构差异
> 对于不支持的版本会抛出UnsupportedVersionException异常
