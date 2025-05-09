# URIBuilder

## 基本信息
- 类名和包路径: taboolib.expansion.URIBuilder
- 基本用途: 构建Redis连接URI和客户端配置的工具类，支持DSL风格配置
- 类型: 类(Class)和顶层函数(Top-level functions)
- 所属模块: database-lettuce-redis

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> formConfig(config: ConfigurationSection): LettuceClientConverter -> 从配置节点创建Redis客户端转换器
> buildClient(action: URIBuilder.() -> Unit): LettuceClientConverter -> 使用DSL构建Redis客户端转换器的顶层函数
> buildURI(action: URIBuilder.() -> Unit): RedisURI -> 使用DSL构建Redis URI的顶层函数

### 类内可被访问字段
> redisURI: RedisURI.Builder -> Redis URI构建器
> urlObj: RedisURI? -> 直接通过字符串创建的Redis URI对象
> poolTwoConfig: GenericObjectPoolConfig<StatefulRedisConnection<String, String>> -> 同步连接池配置
> poolLettuceConfig: BoundedPoolConfig.Builder -> 异步连接池配置

### 类方法
> input(value: String): Unit -> 直接设置Redis URI字符串
> String.link(port: Int): URIBuilder -> 设置主机和端口的扩展函数
> password(password: String): URIBuilder -> 设置密码
> database(database: Int): URIBuilder -> 设置数据库索引
> timeout(timeout: Duration): URIBuilder -> 设置连接超时时间
> ssl(ssl: Boolean): URIBuilder -> 设置是否使用SSL
> host(host: String): URIBuilder -> 设置主机地址
> port(port: Int): URIBuilder -> 设置端口
> setMasterHost(masterHost: String): URIBuilder -> 设置主从模式的主节点ID
> build(): LettuceClientConverter -> 构建Redis客户端转换器
> getURI(): RedisURI -> 获取构建的Redis URI
> maxTotal(maxTotal: Int): URIBuilder -> 设置连接池最大连接数
> maxIdle(maxIdle: Int): URIBuilder -> 设置连接池最大空闲连接数
> minIdle(minIdle: Int): URIBuilder -> 设置连接池最小空闲连接数
> maxWait(maxWait: Duration): URIBuilder -> 设置连接池最大等待时间

## 实现细节
- 提供了DSL风格的API，使用Kotlin的函数扩展特性简化配置
- 支持两种方式创建Redis URI：通过builder逐步构建或直接通过字符串创建
- 支持配置两种连接池：基于Apache Commons Pool2的同步连接池和Lettuce的异步连接池
- 从配置文件创建时，支持多种配置项，包括主机、端口、密码、SSL、超时、数据库索引等
- 支持主从模式的配置，可以设置主节点ID
- 直接通过URI字符串创建的配置优先级高于逐步构建的配置

## 使用场景
> 需要以编程方式配置Redis连接的场景
> 需要从配置文件加载Redis连接配置的场景
> 需要配置Redis连接池的场景
> 需要支持不同Redis部署模式(单机、主从、集群)的场景

## 注意事项
> 密码使用字符数组存储而非字符串，避免在内存中长时间保留敏感信息
> 直接通过URI字符串创建的配置会覆盖其他单独设置的配置项
> 异步连接池不支持设置最大等待时间
> 从配置文件创建时，host是必需的配置项，否则会抛出异常
