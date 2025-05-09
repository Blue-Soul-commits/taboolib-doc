# InventoryHandler

## 基本信息
- 类名和包路径: taboolib.module.ui.virtual.InventoryHandler
- 基本用途: 处理虚拟背包的核心逻辑，包括数据包处理、背包打开关闭等操作
- 类型: 抽象类
- 所属模块: bukkit-ui

## 类结构

### 公开静态字段
> instance: InventoryHandler -> 通过nmsProxy获取的InventoryHandler实例
> playerContainerCounterMap: ConcurrentHashMap<String, Int> -> 玩家容器计数器映射
> playerRemoteInventoryMap: ConcurrentHashMap<String, RemoteInventory> -> 玩家远程背包映射

### 公开静态方法
> getContainerCounter(player: Player, updateId: Boolean = true): Int -> 获取玩家容器计数器，可选是否更新ID

### 类内可被访问字段
> 无

### 类方法
> craftChatMessageToPlain(message: Any): String -> 将NMS聊天组件转换为纯文本
> parseToCraftChatMessage(source: String): Any -> 将字符串解析为NMS聊天组件
> openInventory(player: Player, inventory: VirtualInventory, cursorItem: ItemStack = player.itemOnCursor, updateId: Boolean = true): RemoteInventory -> 为玩家打开虚拟背包

## 实现细节
- 使用nmsProxy获取适合当前Minecraft版本的InventoryHandler实现
- 通过监听数据包事件处理玩家与虚拟背包的交互
- 使用ConcurrentHashMap存储玩家相关数据，保证线程安全
- 在玩家退出或插件禁用时清理相关资源

## 使用场景
> 创建和管理虚拟背包界面
> 处理玩家与虚拟背包的交互，如点击、关闭等操作
> 处理铁砧重命名事件

## 注意事项
> 由于涉及NMS操作，需要注意不同Minecraft版本的兼容性
> 使用@Ghost注解标记的方法在某些环境下可能不会被调用
> 在处理数据包时需要考虑不同版本的字段名差异
