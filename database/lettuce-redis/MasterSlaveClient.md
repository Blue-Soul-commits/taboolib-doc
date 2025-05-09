# MasterSlaveClient

## 基本信息
- 类名和包路径: taboolib.expansion.client.impl.MasterSlaveClient
- 基本用途: Redis主从模式客户端实现，支持同步/异步/响应式操作和发布订阅功能
- 类型: 类(Class)
- 所属模块: database-lettuce-redis

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> redisURI: URIBuilder -> Redis连接URI构建器，包含连接参数和连接池配置
> pool: PoolType -> 连接池类型(NONE/SYNC/ASYNC)
> sync: RedisCommands<String, String> -> 同步命令接口
> async: RedisAsyncCommands<String, String> -> 异步命令接口
> reactive: RedisReactiveCommands<String, String> -> 响应式命令接口
> client: RedisClient -> Lettuce Redis客户端实例
> connection: StatefulRedisMasterReplicaConnection<String, String> -> 主从连接
> poolObj: GenericObjectPool<StatefulRedisConnection<String, String>>? -> 同步连接池对象
> asyncPool: BoundedAsyncPool<StatefulRedisConnection<String, String>>? -> 异步连接池对象
> connectionPubSub: StatefulRedisPubSubConnection<String, String> -> 发布订阅连接

### 类方法
> connect(vararg uri: RedisURI): Unit -> 连接到主从节点
> readForm(form: ReadFrom): Unit -> 设置读取策略
> close(): Unit -> 关闭连接和资源
> subscribeSync(vararg channels: String): Unit -> 同步订阅频道
> subscribeAsync(vararg channels: String): Unit -> 异步订阅频道
> subscribeReactive(vararg channels: String): Unit -> 响应式订阅频道
> addListener(action: LettucePubSubListener): Unit -> 添加发布订阅监听器
> removeListener(action: LettucePubSubListener): Unit -> 移除发布订阅监听器

## 实现细节
- 实现了IRedisClient、IRedisMultiple、IRedisCommand、IPubSubConnection和Closeable接口
- 支持三种连接池模式：无连接池(NONE)、同步连接池(SYNC)和异步连接池(ASYNC)
- 使用Lettuce的MasterReplica功能创建主从连接
- 支持设置读取策略(ReadFrom)，可以控制从主节点还是从节点读取数据
- 提供同步、异步和响应式三种操作模式
- 支持Redis发布订阅功能，可以添加和移除监听器
- 在关闭时会根据连接池类型选择不同的关闭方式
- 注释指出在MasterSlaveClient中使用异步连接池不合理，但仍然提供了实现

## 使用场景
> 连接Redis主从架构的场景
> 需要同步/异步/响应式操作Redis的场景
> 需要控制读取策略(从主节点或从节点读取)的场景
> 需要使用Redis发布订阅功能的场景
> 需要连接池管理Redis连接的场景

## 注意事项
> 使用前需要先调用connect方法连接到从节点
> 使用ASYNC连接池模式时，需要手动获取连接并执行操作
> 在使用前需要确保sync、async和reactive字段已经初始化
> 关闭客户端时会释放所有资源，包括连接池和发布订阅连接
> 发布订阅连接与普通命令连接是分开的，需要单独管理
> 方法名readForm应该是readFrom的拼写错误，但保持一致性
