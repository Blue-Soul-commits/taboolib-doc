# IRedisCommand

## 基本信息
- 类名和包路径: taboolib.expansion.client.IRedisCommand
- 基本用途: 提供Redis命令操作的统一接口，支持同步、异步和反应式三种操作模式
- 类型: 接口(Interface)
- 所属模块: database-lettuce-redis

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> sync: RedisCommands<String, String> -> 同步命令源，用于执行同步Redis操作
> async: RedisAsyncCommands<String, String> -> 异步命令源，用于执行异步Redis操作
> reactive: RedisReactiveCommands<String, String> -> 反应式命令源，用于执行反应式Redis操作

### 类方法
> sync(block: RedisCommands<String, String>.() -> Any): Any -> 执行同步Redis命令的函数式接口
> async(block: RedisAsyncCommands<String, String>.() -> Any): Any -> 执行异步Redis命令的函数式接口
> reactive(block: RedisReactiveCommands<String, String>.() -> Any): Any -> 执行反应式Redis命令的函数式接口

## 实现细节
- 接口将Redis的K-V类型限定为String类型，简化了开发逻辑
- 提供了三种不同的操作模式：同步(sync)、异步(async)和反应式(reactive)
- 每种操作模式都提供了函数式接口，允许使用Kotlin的DSL风格编写Redis操作代码
- 实现类包括SingleClient、MasterSlaveClient和ClusterClient，分别对应不同的Redis部署模式

## 使用场景
> 需要在应用中集成Redis操作，并根据不同场景选择合适的操作模式
> 需要统一管理Redis连接和操作的场景
> 需要支持不同Redis部署模式(单机、主从、集群)的场景

## 注意事项
> 接口将K-V类型限定为String，如需其他类型支持需要自行序列化和反序列化
> 使用时需要选择合适的操作模式，同步模式会阻塞当前线程，异步和反应式则不会
> 实现类需要正确管理Redis连接资源，避免资源泄漏
