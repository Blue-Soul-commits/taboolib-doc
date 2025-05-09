# IRedisMultiple

## 基本信息
- 类名和包路径: taboolib.expansion.client.IRedisMultiple
- 基本用途: 提供Redis多节点连接的统一接口，用于主从复制和集群模式
- 类型: 接口(Interface)
- 所属模块: database-lettuce-redis

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> 无

### 类方法
> connect(vararg uri: RedisURI): Unit -> 连接到多个Redis节点，用于主从复制或集群模式

## 实现细节
- 接口定义了连接到多个Redis节点的方法
- 使用可变参数(vararg)支持任意数量的Redis节点URI
- 主要实现类为MasterSlaveClient，用于主从复制模式
- 在ClusterClient中也有类似实现，但使用的是不同的参数格式

## 使用场景
> 需要配置Redis主从复制模式的场景
> 需要连接到多个Redis节点形成集群的场景
> 需要在运行时动态添加Redis节点的场景

## 注意事项
> 连接多个节点时，第一个节点通常被视为主节点
> 在主从模式下，需要正确配置读写分离策略
> 实现类需要正确管理多个Redis连接资源，避免资源泄漏
