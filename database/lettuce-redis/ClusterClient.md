# ClusterClient

## 基本信息
- 类名和包路径: taboolib.expansion.client.impl.ClusterClient
- 基本用途: Redis集群模式客户端实现，支持同步/异步/响应式操作和发布订阅功能
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
> clusterMap: ConcurrentHashMap<String, Pair<String, Int>> -> 集群节点名称到主机和端口的映射
> connection: StatefulRedisClusterConnection<String, String> -> 集群连接
> clusterClient: RedisClusterClient -> Lettuce Redis集群客户端实例
> poolObj: GenericObjectPool<StatefulRedisClusterConnection<String, String>>? -> 同步连接池对象
> asyncPool: CompletionStage<BoundedAsyncPool<StatefulRedisClusterConnection<String, String>>>? -> 异步连接池对象

### 类方法
> connect(vararg uriBuilder: Pair<String, RedisURI>): Unit -> 连接到集群节点
> getSubCluster(host: String, port: Int): StatefulRedisConnection<String, String>? -> 获取指定主机和端口的节点连接
> getSubCluster(name: String): StatefulRedisConnection<String, String>? -> 获取指定名称的节点连接
> enableTopologyRefresh(time: Duration): Unit -> 启用周期性拓扑刷新
> enableAdaptiveTopologyRefresh(time: Duration): Unit -> 启用自适应拓扑刷新
> async(block: RedisAdvancedClusterAsyncCommands<String, String>.() -> Any): Any -> 执行异步命令
> async(host: String, port: Int, block: StatefulRedisConnection<String, String>.() -> Any): Any -> 在指定节点执行异步命令
> async(name: String, block: StatefulRedisConnection<String, String>.() -> Any): Any -> 在指定名称的节点执行异步命令
> sync(block: RedisAdvancedClusterCommands<String, String>.() -> Any): Any -> 执行同步命令
> sync(host: String, port: Int, block: StatefulRedisConnection<String, String>.() -> Any): Any -> 在指定节点执行同步命令
> sync(name: String, block: StatefulRedisConnection<String, String>.() -> Any): Any -> 在指定名称的节点执行同步命令
> reactive(block: RedisAdvancedClusterReactiveCommands<String, String>.() -> Any): Any -> 执行响应式命令
> reactive(host: String, port: Int, block: StatefulRedisConnection<String, String>.() -> Any): Any -> 在指定节点执行响应式命令
> reactive(name: String, block: StatefulRedisConnection<String, String>.() -> Any): Any -> 在指定名称的节点执行响应式命令
> close(): Unit -> 关闭连接和资源
> subscribeSync(vararg channels: String): Unit -> 同步订阅频道
> subscribeAsync(vararg channels: String): Unit -> 异步订阅频道
> subscribeReactive(vararg channels: String): Unit -> 响应式订阅频道
> addListener(action: LettucePubSubListener): Unit -> 添加发布订阅监听器
> removeListener(action: LettucePubSubListener): Unit -> 移除发布订阅监听器

## 实现细节
- 实现了IRedisClient、IPubSubConnection和Closeable接口
- 支持三种连接池模式：无连接池(NONE)、同步连接池(SYNC)和异步连接池(ASYNC)
- 使用ConcurrentHashMap存储集群节点名称到主机和端口的映射，便于通过名称访问节点
- 支持周期性和自适应两种拓扑刷新模式，用于自动发现和更新集群节点
- 提供同步、异步和响应式三种操作模式，可以针对整个集群或特定节点执行命令
- 支持Redis发布订阅功能，可以添加和移除监听器
- 在关闭时会根据连接池类型选择不同的关闭方式

## 使用场景
> 连接Redis集群的场景
> 需要同步/异步/响应式操作Redis集群的场景
> 需要针对特定集群节点执行命令的场景
> 需要自动发现和更新集群拓扑的场景
> 需要使用Redis发布订阅功能的场景

## 注意事项
> 使用前需要先调用connect方法连接到集群节点
> 使用ASYNC连接池模式时，需要手动获取连接并执行操作
> 通过名称访问节点前，需要确保该名称已在connect方法中注册
> 启用拓扑刷新可能会增加网络开销，但可以提高集群可用性
> 关闭客户端时会释放所有资源，包括连接池和发布订阅连接

