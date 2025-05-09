# VirtualInventory

## 基本信息
- 类名和包路径: taboolib.module.ui.virtual.VirtualInventory
- 基本用途: 虚拟物品栏实现，用于创建可远程操作的物品栏界面
- 类型: 实现类
- 所属模块: taboolib.module.ui.virtual

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> remoteInventory: RemoteInventory? -> 远程背包实例
> storageContents: List<ItemStack>? -> 玩家背包内容
> bukkitInventory: Inventory -> 被包装的原始物品栏

### 类方法
> initStorageItems(): Unit -> 初始化玩家背包内容
> getStorageItem(slot: Int): ItemStack -> 获取玩家背包内容
> getStorageItems(): List<ItemStack> -> 获取玩家背包内容列表
> setStorageItem(slot: Int, item: ItemStack?): Unit -> 设置玩家背包内容
> setStorageItems(items: List<ItemStack>): Unit -> 设置玩家背包内容列表
> getTitle(): String -> 获取物品栏标题
> 以及所有实现自Inventory接口的方法

## 实现细节
- 实现了Bukkit的Inventory接口，可以作为标准物品栏使用
- 包装了一个真实的Bukkit物品栏实例(bukkitInventory)，所有操作都会委托给它
- 维护了玩家背包内容(storageContents)，用于模拟玩家背包部分
- 当设置storageContents时，如果长度不足36，会自动补充空气方块
- 在初始化时检查是否重复包装VirtualInventory，防止递归包装
- 当调用setItem或setContents方法时，会通过remoteInventory发送数据包更新客户端显示
- 提供getTitle方法用于兼容老版本Minecraft，某些插件会调用此方法

## 使用场景
> 创建自定义物品栏界面，需要完全控制玩家交互
> 实现远程物品栏操作，如跨服物品栏同步
> 需要监控和拦截物品栏操作的场景
> 创建虚拟的物品栏界面，不依赖于实体方块

## 注意事项
> VirtualInventory不能被再次包装，会抛出错误
> 在调用initStorageItems前，必须确保remoteInventory已设置或storageContents已初始化
> 所有对物品栏的修改都会通过数据包发送给客户端，不会直接修改玩家的真实物品栏
> 使用前需要通过openVirtualInventory方法打开，而不是直接使用openInventory

