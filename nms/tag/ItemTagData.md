# ItemTagData

## 基本信息
- 类名和包路径: taboolib.module.nms.ItemTagData
- 基本用途: Minecraft NBT 数据的抽象表示，支持各种 NBT 数据类型
- 类型: 开放类 (open class)
- 所属模块: bukkit-nms-tag

## 类结构

### 构造函数
> 主构造函数: ItemTagData(val type: ItemTagType, protected var data: Any)
> 12个次构造函数，分别对应不同的数据类型:
  - Byte, Short, Int, Long, Float, Double (基本数值类型)
  - ByteArray, IntArray, LongArray (数组类型)
  - String (字符串类型)
  - ItemTagList (列表类型)
  - ItemTag (复合类型)

### 属性
> type: ItemTagType -> NBT 数据的类型
> data: Any -> 受保护的内部数据存储

### 类型转换方法
> asByte(), asShort(), asInt(), asLong() -> 转换为基本数值类型
> asFloat(), asDouble() -> 转换为浮点数类型
> asByteArray(), asIntArray(), asLongArray() -> 转换为数组类型
> asString() -> 转换为字符串
> asList() -> 转换为 ItemTagList
> asCompound() -> 转换为 ItemTag (复合类型)
> unsafeData() -> 直接获取内部数据

### JSON 相关方法
> toJsonSimplified(): String -> 转换为简化的 JSON 格式 (不可逆)
> toJsonSimplified(index: Int): String -> 带缩进的 JSON 格式化

### 其他方法
> clone(): ItemTagData -> 深度克隆当前数据
> toString(): String -> 转换为字符串 (调用 saveToString())
> equals(other: Any?): Boolean -> 比较两个 ItemTagData 是否相等
> hashCode(): Int -> 获取哈希码

### 伴生对象方法
> toNBT(obj: Any?): ItemTagData -> 将任意对象转换为 ItemTagData
> translateList(itemTagList: ItemTagList, anyList: List<*>): ItemTagList -> 将普通列表转换为 ItemTagList
> translateSection(itemTag: ItemTag, bukkitSection: ConfigurationSection): ItemTag -> 将 Bukkit 配置部分转换为 ItemTag

## 实现细节
- 使用 taboolib.common5 包中的扩展属性 (cbyte, cshort 等) 进行类型转换
- clone() 方法根据不同类型实现深拷贝，确保数据独立性
- 对于复合类型和列表类型，递归克隆其中的每个元素
- toNBT() 方法支持多种类型的自动转换，包括基本类型、集合类型和 Bukkit 配置
- 特殊处理字符串中的短整型格式 (如 "123s")

## 使用场景
> 在 Minecraft 插件中处理物品的 NBT 数据
> 在配置文件和 NBT 数据之间进行转换
> 在内存中表示和操作 NBT 数据结构
> 作为 ItemTag 和 ItemTagList 的基类，提供通用功能

## 注意事项
> 类型转换方法可能会抛出类型转换异常，使用前应确认数据类型
> 克隆复杂数据结构可能会消耗较多资源
> 对于大型 NBT 数据，应注意内存使用
> saveToString() 方法依赖于 NMSItemTag.instance 实现

