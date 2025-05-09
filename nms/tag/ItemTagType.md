# ItemTagType

## 基本信息
- 类名和包路径: taboolib.module.nms.ItemTagType
- 基本用途: 定义 Minecraft NBT 数据类型的枚举
- 类型: 枚举类
- 所属模块: bukkit-nms-tag

## 类结构

### 枚举值
> END(0) -> 表示 NBT 标签的结束
> BYTE(1) -> 字节类型，1 字节
> SHORT(2) -> 短整型，2 字节
> INT(3) -> 整型，4 字节
> LONG(4) -> 长整型，8 字节
> FLOAT(5) -> 单精度浮点型，4 字节
> DOUBLE(6) -> 双精度浮点型，8 字节
> BYTE_ARRAY(7) -> 字节数组
> STRING(8) -> 字符串
> LIST(9) -> 列表，包含相同类型的多个 NBT 标签
> COMPOUND(10) -> 复合标签，包含不同类型的多个 NBT 标签
> INT_ARRAY(11) -> 整型数组
> LONG_ARRAY(12) -> 长整型数组

### 字段
> id: Byte -> NBT 类型的数字标识符，使用 @JvmField 注解使其在 Java 中可直接访问

### 伴生对象方法
> parse(input: String): ItemTagType -> 将字符串解析为 ItemTagType 枚举值，如果解析失败则返回 END

## 实现细节
- 使用 Google Guava 库的 `Enums.getIfPresent` 方法安全地解析字符串为枚举值
- 如果解析失败，返回 END 作为默认值
- 每个枚举值都对应一个字节 ID，与 Minecraft NBT 规范一致

## 使用场景
> 在处理 Minecraft NBT 数据时，用于标识不同类型的 NBT 标签
> 在 ItemTag 系统中，用于确定 ItemTagData 的类型
> 在序列化和反序列化 NBT 数据时，用于判断数据类型

## 注意事项
> 枚举值的顺序和 ID 与 Minecraft NBT 规范一致，不应更改
> LONG_ARRAY(12) 类型在 Minecraft 1.12 及以上版本才支持
> 在处理不同版本的 Minecraft 时，需要注意版本兼容性
