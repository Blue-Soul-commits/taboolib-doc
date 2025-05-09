# ItemTag

## 基本信息
- 类名和包路径: taboolib.module.nms.ItemTag
- 基本用途: Minecraft NBT 复合标签的抽象表示，用于操作物品的 NBT 数据
- 类型: 开放类 (open class)，继承自 ItemTagData，实现 MutableMap 接口
- 所属模块: bukkit-nms-tag

## 类结构

### 构造函数
> 无参构造函数: 创建空的 ItemTag
> Map 构造函数: 从已有的 Map<String, ItemTagData> 创建 ItemTag

### 核心功能
> 物品 NBT 操作:
  - saveTo(item: ItemStack, onlyCustom: Boolean): 将 NBT 数据写入物品
  - toJson()/toJsonFormatted(): 转换为 JSON 字符串
  - toJsonSimplified(): 转换为可读的简化 JSON 格式

> 深度操作方法:
  - getDeep(key: String): 深度获取嵌套结构中的数据
  - putDeep(key: String, value: Any?): 深度写入嵌套结构中的数据
  - removeDeep(key: String): 深度删除嵌套结构中的数据
  - getDeepOrElse(key: String, base: ItemTagData): 深度获取数据，不存在时返回默认值
  - getDeepWith(key: String, create: Boolean, action: (ItemTag) -> ItemTagData?): 内部辅助函数

> Map 接口实现:
  - 标准 Map 操作: get, put, remove, containsKey, containsValue, isEmpty 等
  - 扩展操作: set 操作符重载，支持任意类型值和深度路径

### 伴生对象方法
> empty(): 创建空的 ItemTag 实例
> toJson(item: ItemStack): 将物品转换为 JSON 字符串
> toItem(json: String): 从 JSON 字符串创建物品
> fromJson(json: String)/fromJson(element: JsonElement): 从 JSON 创建 ItemTag
> fromLegacyJson(json: String)/fromLegacyJson(element: JsonElement): 从旧版 JSON 格式创建 ItemTag

## 实现细节
- 使用 ConcurrentHashMap 存储键值对，确保线程安全
- 支持点号分隔的路径表示法访问嵌套结构 (如 "a.b.c")
- 特殊处理 UUID 和 Boolean 类型，将其转换为字符串存储
- 通过 ItemTagSerializer 实现 JSON 序列化和反序列化
- 支持新旧两种 JSON 格式，确保向后兼容性
- 在 1.20.5+ 版本中，支持完整物品数据的序列化和反序列化

## 使用场景
> 读取和修改 Minecraft 物品的 NBT 数据
> 在插件配置和数据库中存储和恢复物品数据
> 创建和修改具有复杂 NBT 结构的自定义物品
> 在不同 Minecraft 版本间提供统一的 NBT 操作接口

## 注意事项
> saveTo() 方法会直接修改传入的物品，而不是创建新的物品
> 在 1.20.5 以上版本中，onlyCustom 参数决定是否只操作自定义数据
> 在低版本中，toItem() 方法创建的物品默认为 STONE 类型
> 使用深度操作方法时，路径中的每个部分都必须是复合类型 (ItemTag)

