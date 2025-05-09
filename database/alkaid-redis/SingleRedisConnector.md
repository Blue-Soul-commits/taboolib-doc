# SingleRedisConnector

## 基本信息
- 类名和包路径: taboolib.expansion.SingleRedisConnector
- 基本用途: Redis单机模式连接器，用于建立和管理Redis单机模式的连接
- 类型: 类(Class)
- 所属模块: database-alkaid-redis

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> host: String -> Redis服务器地址，默认"127.0.0.1"
> port: Int -> Redis服务器端口，默认6379
> auth: String? -> Redis认证用户名，默认null
> pass: String? -> Redis认证密码，默认null
> connect: Int -> 连接池大小，默认32
> timeout: Int -> 连接超时时间，默认1000毫秒
> reconnectDelay: Long -> 重连延迟时间，默认1000毫秒
> pool: JedisPool? -> Jedis连接池实例，内部使用
> config: JedisPoolConfig -> Jedis连接池配置，内部使用

### 类方法
> connect(): SingleRedisConnector -> 连接到Redis服务器
> close() -> 关闭Redis连接
> connection(): SingleRedisConnection -> 获取Redis连接
> host(host: String): SingleRedisConnector -> 设置Redis服务器地址
> port(port: Int): SingleRedisConnector -> 设置Redis服务器端口
> auth(auth: String?): SingleRedisConnector -> 设置Redis认证用户名
> pass(pass: String?): SingleRedisConnector -> 设置Redis认证密码
> connect(connect: Int): SingleRedisConnector -> 设置连接池大小
> timeout(timeout: Int): SingleRedisConnector -> 设置连接超时时间
> reconnectDelay(reconnectDelay: Long): SingleRedisConnector -> 设置重连延迟时间

## 实现细节
- 使用JedisPool实现Redis连接池管理
- 支持用户名密码认证
- 提供流式API，所有设置方法都返回this引用
- 实现Closeable接口，支持资源自动关闭
- 连接池配置可自定义，包括连接池大小等参数

## 使用场景
> Redis单机连接：用于连接单机模式的Redis服务器
> 数据缓存：在应用中使用Redis作为缓存层
> 会话存储：存储用户会话信息
> 消息队列：实现简单的消息队列功能

## 注意事项
> 使用前必须调用connect()方法建立连接
> 使用完毕后应调用close()方法释放资源
> 在获取connection()之前必须先connect()，否则会抛出异常
> 重连机制在SingleRedisConnection中实现，而不是在连接器中

