# ClusterRedisConnector

## 基本信息
- 类名和包路径: taboolib.expansion.ClusterRedisConnector
- 基本用途: Redis集群连接器，用于建立和管理Redis集群模式的连接
- 类型: 类(Class)
- 所属模块: database-alkaid-redis

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> auth: String? -> Redis认证用户名
> pass: String? -> Redis认证密码
> connect: Int -> 连接池大小，默认32
> timeout: Int -> 连接超时时间，默认1000毫秒
> reconnectDelay: Long -> 重连延迟时间，默认1000毫秒
> maxAttempts: Int -> 最大重试次数，默认20次
> clientName: String -> 客户端名称，默认"default"
> cluster: JedisCluster -> Jedis集群客户端实例
> nodes: LinkedHashSet<HostAndPort> -> 集群节点列表
> genericObjectPoolConfig: GenericObjectPoolConfig<Connection> -> 连接池配置

### 类方法
> build(): ClusterRedisConnector -> 构建Redis集群连接
> close() -> 关闭Redis集群连接
> connection(): ClusterRedisConnection -> 获取Redis集群连接
> connection(action: ClusterRedisConnection.() -> Unit): ClusterRedisConnection -> 获取Redis集群连接并执行操作
> addNode(node: String): ClusterRedisConnector -> 添加集群节点

## 实现细节
- 使用JedisCluster实现Redis集群连接
- 支持用户名密码认证
- 提供连接池配置，可自定义连接池大小
- 支持多节点集群配置，通过addNode方法添加节点
- 实现Closeable接口，支持资源自动关闭

## 使用场景
> Redis集群连接：用于连接Redis集群模式的服务器
> 高可用性数据存储：利用Redis集群的高可用特性进行数据存储
> 分布式缓存：在分布式系统中使用Redis集群作为缓存层

## 注意事项
> 使用前必须添加至少一个集群节点，否则无法建立连接
> 必须调用build()方法完成连接的构建
> 使用完毕后应调用close()方法释放资源
> 集群模式下，Redis的某些命令可能不可用或行为有所不同

