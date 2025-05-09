# Converters
## 基本信息
- 类名和包路径: taboolib.module.configuration.Converters (包含 MapConverter 和 UUIDConverter)
- 基本用途: 提供配置系统中常用数据类型的转换器
- 类型: 类文件 (包含多个转换器类)
- 所属模块: basic-configuration

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> 无

### 类方法
#### MapConverter
> convertToField(config: Map<*, *>): Map<*, *> -> 将配置映射转换为字段映射
> convertFromField(map: Map<*, *>): Map<*, *> -> 将字段映射转换为配置映射

#### UUIDConverter
> convertToField(value: String): UUID -> 将字符串转换为 UUID
> convertFromField(value: UUID): String -> 将 UUID 转换为字符串

## 实现细节
- 实现了 NightConfig 库的 Converter 接口，用于配置系统中的类型转换
- MapConverter 提供了 Map 类型的转换支持，在当前实现中直接返回原始映射
- UUIDConverter 提供了 UUID 和字符串之间的双向转换
- 这些转换器可以在 NightConfig 的对象转换系统中使用，支持自定义类型的序列化和反序列化

## 使用场景
> 在配置系统中处理 Map 类型的数据
> 在配置文件中存储和读取 UUID 类型的数据
> 为 ObjectConverter 提供自定义类型的转换支持
> 在对象与配置之间的转换过程中处理特殊类型

## 注意事项
> MapConverter 当前实现简单地返回原始映射，可能在某些复杂场景下需要更深层次的转换
> UUIDConverter 依赖于 UUID.fromString() 方法，如果字符串格式不正确会抛出异常
> 这些转换器通常由配置系统内部使用，很少需要直接操作
> 可以参考这些转换器实现自定义类型的转换器
