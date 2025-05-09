# RedisCache

## 基本信息
- 类名和包路径: taboolib.expansion.tool.RedisCache
- 基本用途: Redis缓存工具类，提供简单易用的Redis缓存操作接口，支持本地缓存回退
- 类型: 对象(Object)
- 所属模块: database-alkaid-redis-tool

## 类结构

### 公开静态字段
> json: ObjectMapper -> Jackson JSON序列化工具，懒加载

### 公开静态方法
> load() -> 加载Jackson-Kotlin模块依赖
> jsonMapper(): ObjectMapper -> 获取JSON序列化工具
> check() -> 定时清理过期本地缓存
> link(configuration: Configuration) -> 连接Redis服务器
> get(key: String): String? -> 获取缓存值
> getObject<T>(key: String): T? -> 获取并反序列化缓存对象
> set(key: String, value: String) -> 设置缓存值
> setCacheObject(key: String, value: Any) -> 序列化并缓存对象
> setCacheObject(key: String, value: Any, seconds: Long, timeUnit: TimeUnit) -> 序列化并缓存对象，带过期时间
> del(key: String) -> 删除缓存
> delPrefix(prefix: String) -> 删除指定前缀的所有缓存
> setExpire(key: String, seconds: Long, timeUnit: TimeUnit) -> 设置缓存过期时间
> setEx(key: String, value: String, seconds: Long, timeUnit: TimeUnit) -> 设置缓存值并设置过期时间

### 类内可被访问字段
> connector: SingleRedisConnector? -> Redis连接器
> connection: SingleRedisConnection? -> Redis连接
> isEnable: Boolean -> Redis是否启用
> cache: ConcurrentHashMap<String, CacheData> -> 本地缓存

### 类内方法
> getConnection(): SingleRedisConnection -> 安全获取Redis连接，失败时自动重连

## 实现细节
- 使用@Inject注解标记为依赖注入组件
- 使用@RuntimeDependencies声明Jackson相关依赖
- 支持Redis和本地缓存两种模式，当Redis不可用时自动降级到本地缓存
- 使用Jackson-Kotlin进行对象序列化和反序列化
- 实现了自动重连机制，确保Redis连接可用
- 使用Lua脚本实现批量删除前缀匹配的键
- 本地缓存支持过期时间，并通过定时任务清理过期缓存
- 提供简洁的API，隐藏了Redis操作的复杂性

## 使用场景
> 简单缓存：快速实现应用级缓存，无需关心底层实现
> 对象缓存：直接缓存和获取Kotlin/Java对象，自动处理序列化
> 分布式缓存：在分布式环境中共享缓存数据
> 本地回退：当Redis不可用时自动使用本地缓存，提高可用性
> 批量操作：支持按前缀批量删除缓存

## 注意事项
> 使用前必须调用link()方法初始化
> 本地缓存模式下，缓存不会在多个实例间共享
> 对象序列化依赖Jackson-Kotlin，确保对象可序列化
> 批量删除操作在数据量大时可能影响性能
> 默认情况下缓存不会过期，除非显式设置过期时间
