# RemoteInventory

## 基本信息
- 类名和包路径: taboolib.module.ui.virtual.RemoteInventory
- 基本用途: 提供虚拟背包的远程控制接口，用于管理玩家与虚拟背包的交互
- 类型: 接口
- 所属模块: bukkit-ui

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> inventory: VirtualInventory -> 获取虚拟背包实例
> viewer: Player -> 所属玩家
> id: Int -> 页面序号
> title: String -> 背包标题

### 类方法
> refresh(contents: List<ItemStack>, storageContents: List<ItemStack>? = null, cursorItem: ItemStack = viewer.itemOnCursor): Unit -> 刷新页面内容
> sendSlotChange(slot: Int, itemStack: ItemStack): Unit -> 设置指定槽位的物品
> sendCarriedChange(itemStack: ItemStack): Unit -> 设置光标上的物品
> onClick(callback: ClickEvent.() -> Unit): Unit -> 设置点击事件回调
> onClose(callback: () -> Unit): Unit -> 设置关闭事件回调
> close(sendPacket: Boolean = true): Unit -> 关闭页面
> handleClick(packet: Packet): Unit -> 处理点击数据包

## 实现细节
- 通过网络数据包实现对玩家客户端背包界面的远程控制
- 提供了一系列方法用于管理背包内容和处理玩家交互
- 内部类ClickEvent用于封装点击事件的相关信息

## 使用场景
> 创建虚拟背包界面，不依赖于Bukkit原生背包系统
> 实现自定义背包界面，如商店、菜单等功能
> 在ChestImpl中通过virtualize()方法启用虚拟化页面

## 注意事项
> 虚拟背包系统依赖于NMS包，需要注意版本兼容性
> 关闭页面时需要考虑是否发送数据包(sendPacket参数)
> 在处理点击事件时需要正确解析Packet数据
