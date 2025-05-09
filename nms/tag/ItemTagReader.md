# ItemTagReader

## 基本信息
- 类名和包路径: taboolib.module.nms.ItemTagReader
- 基本用途: 提供简便的方式读取和修改 Minecraft 物品的 NBT 数据
- 类型: 数据类 (data class)
- 所属模块: bukkit-nms-tag

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> itemTag: ItemTag -> 存储和操作的 NBT 数据对象

### 类方法
> getKeys(parent: String = "main"): Set<String> -> 获取指定父节点下的所有键名
> toJson(): String -> 将 ItemTag 转换为 JSON 字符串
> formatJson(): String -> 将 ItemTag 转换为格式化的 JSON 字符串
> loadFormJson(json: String): Unit -> 从 JSON 字符串加载 ItemTag 数据
> getString(key: String, def: String): String -> 获取指定键的字符串值，如果不存在则返回默认值
> getString(key: String): String? -> 获取指定键的字符串值，如果不存在则返回 null
> getInt(key: String, def: Int): Int -> 获取指定键的整数值，如果不存在则返回默认值
> getInt(key: String): Int? -> 获取指定键的整数值，如果不存在则返回 null
> getDouble(key: String, def: Double): Double -> 获取指定键的双精度浮点数值，如果不存在则返回默认值
> getDouble(key: String): Double? -> 获取指定键的双精度浮点数值，如果不存在则返回 null
> getStringList(key: String): List<String> -> 获取指定键的字符串列表，如果不存在则返回空列表
> getDoubleList(key: String): List<Double> -> 获取指定键的双精度浮点数列表，如果不存在则返回空列表
> getBoolean(key: String, def: Boolean): Boolean -> 获取指定键的布尔值，如果不存在则返回默认值
> getBoolean(key: String): Boolean -> 获取指定键的布尔值，如果不存在则返回 false
> getLong(key: String, def: Long): Long -> 获取指定键的长整数值，如果不存在则返回默认值
> getLong(key: String): Long? -> 获取指定键的长整数值，如果不存在则返回 null
> getFloat(key: String, def: Float): Float -> 获取指定键的单精度浮点数值，如果不存在则返回默认值
> getFloat(key: String): Float? -> 获取指定键的单精度浮点数值，如果不存在则返回 null
> getByte(key: String, def: Byte): Byte -> 获取指定键的字节值，如果不存在则返回默认值
> getByte(key: String): Byte? -> 获取指定键的字节值，如果不存在则返回 null
> getUUID(key: String): UUID? -> 获取指定键的 UUID 值，如果不存在则返回 null
> getUUID(key: String, def: UUID): UUID -> 获取指定键的 UUID 值，如果不存在则返回默认值
> write(itemStack: ItemStack): Unit -> 将 ItemTag 数据写入到物品中
> saveToItem(itemStack: ItemStack): Unit -> 将 ItemTag 数据保存到物品中（与 write 功能相同）
> putAll(map: Map<String, Any?>): Unit -> 将 Map 中的所有键值对添加到 ItemTag 中
> set(key: String, value: Any?): Unit -> 设置指定键的值，如果值为 null 则移除该键
> remove(key: String): Unit -> 移除指定键
> close(): ItemTag -> 返回当前的 ItemTag 对象
> containsKey(key: String): Boolean -> 检查是否包含指定键
> containsValue(value: ItemTagData): Boolean -> 检查是否包含指定值

## 实现细节
- 作为数据类实现，包含一个可变的 ItemTag 字段
- 提供了丰富的类型转换方法，支持获取各种基本类型和复合类型的数据
- 支持深层次的键值访问，通过点分隔的路径访问嵌套的 NBT 数据
- 特殊处理了 UUID 和 Boolean 类型，将它们转换为字符串存储
- 提供了 JSON 序列化和反序列化功能

## 使用场景
> 读取物品的 NBT 数据，获取自定义属性或元数据
> 修改物品的 NBT 数据，添加或更新自定义属性
> 在插件中实现物品的持久化存储和加载
> 实现物品的序列化和反序列化，用于配置文件或数据库存储

## 注意事项
> 修改 ItemTag 后需要使用 write 或 saveToItem 方法将更改应用到物品上
> 对于 UUID 和 Boolean 类型，会自动转换为字符串存储
> 使用点分隔的路径可以访问嵌套的 NBT 数据，例如 "attributes.generic.attackDamage"
> 当获取不存在的键时，带默认值的方法会返回默认值，不带默认值的方法会返回 null 或空集合
