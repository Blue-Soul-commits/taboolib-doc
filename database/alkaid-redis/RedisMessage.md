# RedisMessage

## 基本信息
- 类名和包路径: taboolib.expansion.RedisMessage
- 基本用途: Redis发布订阅消息的封装类，提供消息处理和反序列化功能
- 类型: 类(Class)
- 所属模块: database-alkaid-redis

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> channel: String -> 消息所属的频道名称
> message: String -> 消息内容
> pubSub: JedisPubSub -> 内部使用的JedisPubSub对象
> patternMode: Boolean -> 是否为模式匹配订阅

### 类方法
> get<T>(ignoreConstructor: Boolean = false): T -> 将消息反序列化为指定类型的对象
> get<T>(obj: T, ignoreConstructor: Boolean = false): T -> 将消息反序列化到指定的对象实例
> close() -> 取消订阅

## 实现细节
- 封装了Redis发布订阅消息的处理
- 使用Configuration工具类进行JSON反序列化
- 支持泛型类型的反序列化
- 实现了Closeable接口，支持资源自动关闭
- 根据patternMode标志决定使用普通取消订阅还是模式取消订阅

## 使用场景
> 处理Redis发布订阅消息：接收并处理来自Redis频道的消息
> 消息反序列化：将JSON格式的消息反序列化为Java/Kotlin对象
> 动态取消订阅：在消息处理过程中可以选择取消订阅

## 注意事项
> 反序列化需要目标类有合适的构造函数或者设置ignoreConstructor为true
> 取消订阅操作会影响所有使用相同JedisPubSub对象的订阅
> 消息内容必须是有效的JSON格式才能成功反序列化
> 在处理大量消息时应注意性能影响
