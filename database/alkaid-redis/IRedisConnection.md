# IRedisConnection

## 基本信息
- 类名和包路径: taboolib.expansion.IRedisConnection
- 基本用途: 提供Redis数据库连接的统一接口，封装了常用的Redis操作
- 类型: 接口(Interface)
- 所属模块: database-alkaid-redis

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> 无

### 类方法
> eval(script: String, keys: List<String>, args: List<String>): Any? -> 执行Lua脚本，传入键列表和参数列表
> eval(script: String, keyC: Int, args: List<String>): Any? -> 执行Lua脚本，传入键数量和参数列表
> getLock(lockName: String): Lock -> 获取分布式锁对象
> getLock(lockName: String, action: Lock.() -> Unit): Lock -> 获取分布式锁对象并执行操作
> close() -> 关闭Redis连接
> set(key: String, value: String?) -> 设置键值对
> setNx(key: String, value: String?) -> 仅当键不存在时设置键值对
> setEx(key: String, value: String?, seconds: Long, timeUnit: TimeUnit) -> 设置键值对并设置过期时间
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
- 接口定义了Redis操作的基本方法，包括键值操作、集合操作、发布订阅等
- 提供了分布式锁的获取方法，通过`Lock`类实现
- 支持Lua脚本执行，可用于复杂的原子操作
- 支持设置键的过期时间，可指定时间单位
- 支持发布订阅模式，可以使用正则模式匹配频道

## 使用场景
> Redis数据存储与缓存：用于存储和获取键值对数据
> 分布式锁：通过getLock方法获取分布式锁，实现分布式系统的同步
> 消息发布与订阅：实现应用间的消息通信
> 集合操作：管理Redis集合数据结构

## 注意事项
> 接口中的方法可能会抛出Redis连接异常，实现类应当处理这些异常
> 使用分布式锁时需要注意锁的释放，避免死锁
> 发布订阅模式下的消息处理应当考虑异常情况，避免影响订阅线程
> 长时间运行的订阅操作应当在单独的线程中执行
