# Coerce

## 基本信息
- 类名和包路径: taboolib.common5.Coerce
- 基本用途: 用于将未知类型的值转换（强制）为特定目标类型的工具类
- 类型: 最终类（final class）
- 所属模块: common-legacy-api

## 类结构

### 公开静态字段
> listPattern: Pattern -> 用于匹配列表格式字符串的正则表达式模式
> listPairings: String[] -> 列表匹配的开始和结束字符对

### 公开静态方法
> format(value: double): double -> 将双精度浮点数格式化为保留2位小数
> format(value: double, scale: int): double -> 将双精度浮点数格式化为指定小数位数
> format(value: double, scale: int, roundingMode: int): double -> 将双精度浮点数格式化为指定小数位数和舍入模式
> format(value: float, scale: int, roundingMode: int): float -> 将单精度浮点数格式化为指定小数位数和舍入模式
> toString(obj: Object): String -> 将对象转换为字符串
> asString(obj: Object): Optional<String> -> 尝试将对象作为字符串获取
> toList(obj: Object): List<?> -> 将对象转换为列表
> asList(obj: Object): Optional<List<?>> -> 尝试将对象作为列表获取
> toListOf(obj: Object, ofClass: Class<T>): List<T> -> 将对象转换为指定类型的列表
> toBoolean(obj: Object): boolean -> 将对象转换为布尔值
> asBoolean(obj: Object): Optional<Boolean> -> 尝试将对象作为布尔值获取
> toInteger(obj: Object): int -> 将对象转换为整数
> asInteger(obj: Object): Optional<Integer> -> 尝试将对象作为整数获取
> toDouble(obj: Object): double -> 将对象转换为双精度浮点数
> asDouble(obj: Object): Optional<Double> -> 尝试将对象作为双精度浮点数获取
> toFloat(obj: Object): float -> 将对象转换为单精度浮点数
> asFloat(obj: Object): Optional<Float> -> 尝试将对象作为单精度浮点数获取
> toShort(obj: Object): short -> 将对象转换为短整数
> asShort(obj: Object): Optional<Short> -> 尝试将对象作为短整数获取
> toByte(obj: Object): byte -> 将对象转换为字节
> asByte(obj: Object): Optional<Byte> -> 尝试将对象作为字节获取
> toLong(obj: Object): long -> 将对象转换为长整数
> asLong(obj: Object): Optional<Long> -> 尝试将对象作为长整数获取
> toChar(obj: Object): char -> 将对象转换为字符
> asChar(obj: Object): Optional<Character> -> 尝试将对象作为字符获取
> toByteArray(obj: Object): byte[] -> 将对象转换为字节数组
> asByteArray(obj: Object): Optional<byte[]> -> 尝试将对象作为字节数组获取
> toEnum(obj: Object, enumClass: Class<E>): E -> 将对象转换为指定枚举类型，失败时返回第一个枚举常量
> toEnum(obj: Object, enumClass: Class<E>, defaultValue: E): E -> 将对象转换为指定枚举类型，失败时返回指定默认值
> toPseudoEnum(obj: Object, pseudoEnumClass: Class<T>, dictionaryClass: Class<?>, defaultValue: T): T -> 将对象转换为伪枚举类型

### 类内可被访问字段
> 无类内可被访问字段（所有方法都是静态的）

### 类方法
> 私有构造方法，防止实例化
> sanitiseNumber(obj: Object): String -> 清理数字字符串，移除千位分隔符和列表中的其他元素
> listBracketsMatch(candidate: Matcher): boolean -> 检查列表的括号是否匹配
> primitiveArrayToList(obj: Object): List<?> -> 将基本类型数组转换为列表
> parseStringToList(string: String): List<?> -> 将字符串解析为列表

## 实现细节
- Coerce 类是一个工具类，所有方法都是静态的，不能被实例化
- 提供了两种类型的转换方法：to* 方法（始终返回一个值，失败时返回默认值）和 as* 方法（返回 Optional，可能为空）
- 数字转换方法会尝试多种解析策略，包括直接转换、字符串解析和清理后解析
- 列表转换支持各种集合类型、数组和字符串表示的列表（如 "{1,2,3}"）
- 枚举转换支持大小写不敏感的匹配

## 使用场景
> 配置文件数据类型转换，将字符串配置值转换为所需的数据类型
> 用户输入验证和转换，确保输入数据符合预期类型
> API 数据处理，统一处理不同来源的数据
> 跨系统数据交换，确保数据类型的一致性

## 注意事项
> to* 方法在转换失败时会返回默认值（通常为该类型的零值），而不是抛出异常
> as* 方法返回 Optional，需要处理可能的空值情况
> 数字转换方法会尝试清理字符串（如移除千位分隔符），但不会处理拼写的数字（如"one"不会被转换为1）
> 列表转换会尝试解析字符串表示的列表，但格式必须符合预期（如 "{1,2,3}"）
