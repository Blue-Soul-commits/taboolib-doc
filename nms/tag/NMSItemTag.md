# NMSItemTag

## 基本信息
- 类名和包路径: taboolib.module.nms.NMSItemTag
- 基本用途: 提供跨 Minecraft 版本的物品 NBT 数据操作抽象层
- 类型: 抽象类
- 所属模块: bukkit-nms-tag

## 类结构

### 公开静态字段
> instance: NMSItemTag -> 根据当前服务器版本获取的 NMSItemTag 实例

### 公开静态方法
> asNMSCopy(item: ItemStack): Any -> 获取 ItemStack 的 NMS 副本
> asBukkitCopy(item: Any): ItemStack -> 获取 NMS 物品的 Bukkit 副本

### 类内可被访问字段
> 无类内可被访问字段

### 类方法
> newItemTag(): ItemTag -> 生成适配当前版本的 ItemTag
> getNMSCopy(itemStack: ItemStack): Any -> 将 Bukkit ItemStack 转换为 NMS ItemStack
> getBukkitCopy(itemStack: Any): ItemStack -> 将 NMS ItemStack 转换为 Bukkit ItemStack
> getItemTag(itemStack: ItemStack, onlyCustom: Boolean): ItemTag -> 获取物品的 ItemTag
> setItemTag(itemStack: ItemStack, itemTag: ItemTag, onlyCustom: Boolean): ItemStack -> 将 ItemTag 写入物品并返回新物品
> itemTagToString(itemTagData: ItemTagData): String -> 将 ItemTagData 转换为字符串
> itemTagToNMSCopy(itemTagData: ItemTagData): Any -> 将 ItemTagData 转换为 NMS NBTTagCompound
> itemTagToBukkitCopy(nbtTag: Any): ItemTagData -> 将 NMS NBTTag 转换为 ItemTagData
> toMinecraftJson(itemStack: ItemStack): String -> 将物品转换为原版 Json 形式
> fromMinecraftJson(json: String): ItemStack? -> 将原版 Json 转换为物品

## 实现细节
- 使用抽象类定义接口，由不同版本的具体实现类提供实现
- 通过 companion object 提供静态访问点和版本适配逻辑
- 使用 unsafeLazy 延迟初始化实例，根据服务器版本选择合适的实现
- 在 1.20.5+ 版本使用 NMSItemTag12005 实现，在低版本使用 NMSItemTagLegacy 实现
- 提供了扩展函数简化对 ItemStack 和 ItemTagData 的操作

## 使用场景
> 获取和修改物品的 NBT 数据，实现自定义物品属性
> 在不同 Minecraft 版本间提供统一的 NBT 操作接口
> 将物品转换为 JSON 格式用于存储或网络传输
> 在聊天消息中显示物品信息（通过 toMinecraftJson 方法）

## 注意事项
> 在 1.20.5+ 版本中，onlyCustom 参数决定是否只操作自定义数据，而在低版本中此参数无效
> toMinecraftJson 方法在 1.20.5 以下版本不包含物品基本信息，只包含 NBT 数据
> fromMinecraftJson 方法不能接受 ItemTag#toJson 的结果，只能接受原版 JSON 格式
> 操作空物品（null 或 AIR 类型）会抛出异常
