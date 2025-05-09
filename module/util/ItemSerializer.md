# ItemSerializer

## 基本信息
- 类名和包路径: taboolib.platform.util.ItemSerializer
- 基本用途: 提供Bukkit物品和物品栏的序列化与反序列化功能
- 类型: Kotlin扩展函数集合
- 所属模块: bukkit-util

## 类结构

### 公开静态方法
> ByteArray.deserializeToItemStack(zipped: Boolean = true): ItemStack -> 将字节数组反序列化为ItemStack对象
> ItemStack.serializeToByteArray(zipped: Boolean = true): ByteArray -> 将ItemStack对象序列化为字节数组
> ByteArray.deserializeToInventory(inventory: Inventory? = null, zipped: Boolean = true): Inventory -> 将字节数组反序列化为Inventory对象
> Inventory.serializeToByteArray(size: Int = this.size, zipped: Boolean = true): ByteArray -> 将Inventory对象序列化为字节数组

## 实现细节
- 使用Bukkit提供的BukkitObjectInputStream和BukkitObjectOutputStream进行Java序列化
- 支持可选的GZIP压缩，通过taboolib.common.io中的zip和unzip函数实现
- 使用Kotlin的use函数确保资源正确关闭
- 在序列化Inventory时，只保存非空气物品以减小数据大小
- 在反序列化Inventory时，支持填充现有Inventory或创建新的Inventory

## 使用场景
> 需要将物品保存到数据库或配置文件时
> 需要通过网络传输物品数据时
> 实现物品复制或备份功能时
> 开发物品预设或模板系统时
> 实现跨服物品同步功能时

## 注意事项
> 序列化依赖于Java的序列化机制，可能在不同Minecraft版本间不兼容
> 默认启用GZIP压缩以减小数据大小
> 序列化Inventory时只保存非空气物品，但会保留原始槽位信息
> 使用try-with-resources模式确保流正确关闭

