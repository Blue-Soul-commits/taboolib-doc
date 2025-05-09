# AlkaidRedis

## 基本信息
- 类名和包路径: taboolib.expansion.AlkaidRedis
- 基本用途: Redis连接工厂类，提供创建Redis连接器和连接的便捷方法
- 类型: 对象(Object)
- 所属模块: database-alkaid-redis

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> create(): SingleRedisConnector -> 创建Redis单机模式连接器
> linkCluster(builder: ClusterRedisConnector.() -> Unit = {}): ClusterRedisConnector -> 创建Redis集群模式连接器
> createDefault(connector: (SingleRedisConnector) -> Unit = { }): SingleRedisConnection -> 创建默认的Redis连接

### 类内可被访问字段
> 无

### 类方法
> 无（所有方法都是静态方法）

## 实现细节
- 使用@Inject注解标记为依赖注入组件
- 使用@RuntimeDependencies声明运行时依赖，包括：
  - redis.clients:jedis:4.2.3 - Redis Java客户端
  - org.slf4j:slf4j-api:1.7.32 - 日志接口
  - org.apache.commons:commons-pool2:2.11.1 - 连接池库
  - org.json:json:20211205 - JSON处理库
  - com.google.code.gson - Google JSON库
- 所有依赖都设置了relocate规则，避免与其他插件冲突
- 提供工厂方法创建Redis连接器和连接实例
- 支持单机模式和集群模式的Redis连接

## 使用场景
> 快速创建Redis连接：提供简单的API创建Redis连接
> 集群模式支持：支持Redis集群模式的连接创建
> 依赖管理：自动处理Redis客户端的依赖关系
> 插件集成：作为TabooLib插件框架的一部分，提供Redis支持

## 注意事项
> 依赖使用了relocate规则，避免与其他插件的依赖冲突
> 所有依赖都设置了transitive=false，不会加载传递依赖
> 使用前需确保Redis服务器可访问
> 集群模式需要至少3个主节点才能正常工作
