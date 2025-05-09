# ItemTagSerializer

## 基本信息
- 类名和包路径: taboolib.module.nms.ItemTagSerializer
- 基本用途: 提供 ItemTag 相关数据的序列化和反序列化功能
- 类型: 单例对象 (object)
- 所属模块: bukkit-nms-tag

## 类结构

### 公开方法
> serializeTag(tag: ItemTag): JsonObject -> 将 ItemTag 序列化为 JsonObject
> serializeList(tagList: ItemTagList): JsonArray -> 将 ItemTagList 序列化为 JsonArray
> serializeData(tagData: ItemTagData): JsonElement -> 将 ItemTagData 序列化为 JsonElement
> deserializeTag(json: JsonObject): ItemTag -> 将 JsonObject 反序列化为 ItemTag
> deserializeArray(json: JsonArray): ItemTagList -> 将 JsonArray 反序列化为 ItemTagList
> deserializeData(json: JsonElement): ItemTagData -> 将 JsonElement 反序列化为 ItemTagData

## 实现细节
- 序列化过程:
  - 复合类型 (COMPOUND) 递归调用 serializeTag
  - 列表类型 (LIST) 递归调用 serializeList
  - 基本类型添加后缀标识符:
    - BYTE: "b" (例如: "10b")
    - SHORT: "s" (例如: "100s")
    - INT: "i" (例如: "1000i")
    - LONG: "l" (例如: "10000l")
    - FLOAT: "f" (例如: "10.5f")
    - DOUBLE: "d" (例如: "10.5d")
    - STRING/END: "t" (例如: "textt")
  - 数组类型使用逗号分隔元素，并添加类型标识符和右括号:
    - INT_ARRAY: "i]" (例如: "1,2,3i]")
    - BYTE_ARRAY: "b]" (例如: "1,2,3b]")
    - LONG_ARRAY: "l]" (例如: "1,2,3l]")

- 反序列化过程:
  - 根据 JsonElement 类型进行不同处理:
    - JsonArray -> 调用 deserializeArray
    - JsonObject -> 调用 deserializeTag
    - JsonPrimitive -> 根据后缀解析为对应的 ItemTagData
  - 对于字符串类型的 JsonPrimitive:
    - 如果以 "]" 结尾，解析为数组类型
    - 否则根据最后一个字符确定基本类型
  - 使用 NumberConversions 工具类进行类型转换

## 使用场景
> 在需要将 ItemTag 数据转换为 JSON 格式进行存储或传输时使用
> 在需要从 JSON 格式恢复 ItemTag 数据时使用
> 在 ItemTag.toJson() 和 ItemTag.fromJson() 方法中被调用
> 在插件配置文件中存储和读取物品 NBT 数据时使用

## 注意事项
> 序列化格式是自定义的，不是标准的 NBT JSON 格式
> 反序列化时需要处理各种异常情况，如不支持的类型
> 数组类型的序列化格式有特殊处理，需要注意解析逻辑
> 使用 error() 函数抛出异常，调用时需要进行异常处理
