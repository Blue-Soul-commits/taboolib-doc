# SingleRedisConnection

## 基本信息
- 类名和包路径: taboolib.expansion.SingleRedisConnection
- 基本用途: Redis单机模式连接实现类，提供对Redis的各种操作
- 类型: 类(Class)
- 所属模块: database-alkaid-redis

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> pool: JedisPool -> Redis连接池
> connector: SingleRedisConnector -> Redis连接器
> service: ExecutorService -> 用于异步操作的线程池

### 类方法
> exec<T>(loop: Boolean = false, func: (Jedis) -> T): T -> 执行Redis操作，处理连接异常和重连
> eval(script: String, keys: List<String>, args: List<String>): Any? -> 执行Lua脚本，传入键列表和参数列表
> eval(script: String, keyC: Int, args: List<String>): Any? -> 执行Lua脚本，传入键数量和参数列表
> close() -> 关闭Redis连接池
> set(key: String, value: String?) -> 设置键值对
> setNx(key: String, value: String?) -> 仅当键不存在时设置键值对
> get(key: String): String? -> 获取键对应的值
> delete(key: String) -> 删除键
> expire(key: String, value: Long, timeUnit: TimeUnit) -> 设置键的过期时间
> contains(key: String): Boolean -> 检查键是否存在
> publish(channel: String, message: Any) -> 向指定频道发布消息
> subscribe(vararg channel: String, patternMode: Boolean = false, func: RedisMessage.() -> Unit) -> 订阅频道
> createPubSub(patternMode: Boolean, func: RedisMessage.() -> Unit): JedisPubSub -> 创建发布/订阅对象
> sadd(key: String, vararg value: String): Long -> 向集合添加元素
> srem(key: String, vararg value: String): Long -> 从集合移除元素
> scard(key: String): Long -> 获取集合元素数量
> smembers(key: String): Set<String> -> 获取集合所有元素
> sismember(key: String, value: String): Boolean -> 判断元素是否在集合中

## 实现细节
- 实现了IRedisConnection接口，提供Redis操作的统一接口
- 使用JedisPool管理Redis连接
- 实现了自动重连机制，在连接失败时自动重试
- 使用线程池处理异步订阅操作
- 支持Lua脚本执行
- 支持对象序列化为JSON后发布到Redis
- 实现了Closeable接口，支持资源自动关闭
- 使用CopyOnWriteArrayList管理订阅资源，确保在应用关闭时能够正确取消订阅
- 通过@Awake注解在生命周期结束时自动清理资源

## 使用场景
> Redis数据存储：存储和读取键值数据
> 分布式消息发布订阅：实现应用间的消息通信
> 分布式集合操作：管理分布式环境下的集合数据
> 执行Lua脚本：实现复杂的原子操作
> 自动重连：在网络不稳定环境下保持Redis连接可用

## 注意事项
> 使用完毕后应调用close()方法释放资源
> 订阅操作是异步的，在主线程中不会阻塞
> 发布非字符串消息时会自动序列化为JSON
> exec方法提供了自动重连机制，但在极端情况下可能会导致性能问题
> 在处理大量数据时应注意内存使用
