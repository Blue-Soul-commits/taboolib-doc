# LettuceClientConverter

## 基本信息
- 类名和包路径: taboolib.expansion.client.LettuceClientConverter
- 基本用途: Redis客户端转换器，用于创建不同类型的Redis客户端实例
- 类型: 数据类(Data Class)
- 所属模块: database-lettuce-redis

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> redisURI: URIBuilder -> Redis连接URI构建器，包含连接参数和连接池配置

### 类方法
> link<reified T : IRedisClient>(pool: PoolType = PoolType.NONE, builder: T.() -> Unit = {}): T -> 创建指定类型的Redis客户端实例

## 实现细节
- 使用Kotlin的数据类(data class)实现，自动生成equals、hashCode、toString等方法
- 使用泛型和reified类型参数，支持创建不同类型的Redis客户端
- 通过Java反射API创建客户端实例，要求客户端类必须有特定的构造函数
- 支持DSL风格配置，可以在创建客户端后立即进行额外配置
- 默认使用无连接池模式(PoolType.NONE)，也支持同步和异步连接池

## 使用场景
> 需要创建不同类型Redis客户端(单机、主从、集群)的场景
> 需要统一管理Redis客户端创建逻辑的场景
> 需要支持DSL风格配置Redis客户端的场景

## 注意事项
> 客户端类必须实现IRedisClient接口
> 客户端类必须有接受URIBuilder和PoolType参数的构造函数
> 使用反射创建实例，可能会有轻微的性能开销
> 使用inline和reified关键字，避免了运行时类型擦除问题
