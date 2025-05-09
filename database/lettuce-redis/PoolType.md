# PoolType

## 基本信息
- 类名和包路径: taboolib.expansion.client.PoolType
- 基本用途: 定义Redis连接池的类型枚举，用于配置Redis客户端的连接池模式
- 类型: 枚举(Enum)
- 所属模块: database-lettuce-redis

## 类结构

### 公开静态字段
> NONE: PoolType -> 不使用连接池模式
> SYNC: PoolType -> 使用同步阻塞连接池模式，基于Apache Commons Pool2
> ASYNC: PoolType -> 使用异步非阻塞连接池模式

### 公开静态方法
> values(): Array<PoolType> -> 返回包含所有枚举常量的数组
> valueOf(name: String): PoolType -> 返回指定名称的枚举常量

### 类内可被访问字段
> 无

### 类方法
> 无

## 实现细节
- 枚举定义了三种连接池模式，用于配置Redis客户端
- NONE模式不使用连接池，每次操作都创建新连接
- SYNC模式使用Apache Commons Pool2实现的同步阻塞连接池
- ASYNC模式使用Lettuce提供的异步非阻塞连接池

## 使用场景
> 配置Redis客户端连接池类型的场景
> 需要根据性能和资源消耗平衡选择合适连接池模式的场景
> 在配置文件中指定连接池类型的场景

## 注意事项
> NONE模式适用于低频操作，但可能导致连接资源浪费
> SYNC模式适用于高频同步操作，但会阻塞线程
> ASYNC模式适用于高频异步操作，不会阻塞线程，但实现复杂度较高
> 在高并发场景下，应避免使用NONE模式