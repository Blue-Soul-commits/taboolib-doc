# Meta

## 基本信息
- 类名和包路径: taboolib.platform.util.Meta
- 基本用途: 提供Bukkit元数据(Metadata)操作的扩展函数，简化元数据的设置、获取和管理
- 类型: Kotlin扩展函数文件
- 所属模块: bukkit-util

## 类结构

### 公开静态方法
> Metadatable.runMeta(key: String, value: Any = true, func: () -> Unit): Unit -> 在设置元数据的环境中执行函数，执行完毕后自动移除元数据
> Metadatable.runMetaIf(key: String, value: Any = true, func: () -> Boolean): Boolean -> 在元数据不存在时设置元数据并执行函数，执行完毕后自动移除元数据
> Metadatable.setMeta(key: String, value: Any): Unit -> 设置元数据
> Metadatable.hasMeta(key: String): Boolean -> 检查是否存在指定键的元数据
> Metadatable.getMeta(key: String): List<MetadataValue> -> 获取指定键的所有元数据值
> Metadatable.getMetaFirst(key: String): MetadataValue -> 获取指定键的第一个元数据值
> Metadatable.getMetaFirstOrNull(key: String): MetadataValue? -> 获取指定键的第一个元数据值，如果不存在则返回null
> Metadatable.removeMeta(key: String): Unit -> 移除指定键的元数据
> MetadataValue.cast<T>(): T -> 将元数据值转换为指定类型
> MetadataValue.castOrNull<T>(): T? -> 尝试将元数据值转换为指定类型，如果转换失败则返回null

## 实现细节
- 使用Kotlin扩展函数为Bukkit的Metadatable接口提供更简洁的API
- 所有元数据操作都使用TabooLib的BukkitPlugin实例作为插件引用
- runMeta和runMetaIf函数使用try-finally结构确保元数据在函数执行后被清理
- 使用Kotlin的reified泛型实现类型安全的元数据值转换
- 提供可空和非可空版本的元数据获取函数，增强类型安全性

## 使用场景
> 需要临时标记实体或方块状态时
> 实现防重复触发的事件处理时
> 在实体或方块上存储临时数据时
> 实现复杂的交互逻辑时需要状态跟踪
> 开发需要元数据支持的插件功能时

## 注意事项
> 元数据在服务器重启后会丢失，不适合持久化存储
> runMeta和runMetaIf会在函数执行完毕后自动移除元数据，无需手动清理
> getMetaFirst会在元数据不存在时抛出异常，应优先使用getMetaFirstOrNull
> 元数据值可以是任何Java对象，但应注意序列化问题
> 使用cast和castOrNull时应确保类型正确，否则可能抛出ClassCastException

