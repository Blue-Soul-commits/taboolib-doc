# RedisDatabaseHandler

## 基本信息
- 类名和包路径: taboolib.expansion.RedisDatabaseHandler
- 基本用途: 创建和管理Redis数据库连接与数据容器，提供数据库与Redis缓存的交互功能
- 类型: 数据管理器类
- 所属模块: database-player-redis

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> conf: ConfigurationSection -> 配置部分，包含数据库和Redis的连接信息
> table: String -> 数据库表名，默认为插件ID
> database: Database -> 数据库实例，用于持久化存储
> connector: SingleRedisConnector? -> Redis连接器，用于创建Redis连接
> connection: SingleRedisConnection? -> Redis连接，用于执行Redis操作
> redisDataContainer: ConcurrentHashMap<String, RedisDataContainer> -> 玩家Redis数据容器映射表

### 类方法
> setupRedisDataContainer(user: String): RedisDataContainer -> 初始化并返回指定用户的数据容器
> getRedisDataContainer(user: String): RedisDataContainer -> 获取指定用户的数据容器，若不存在则抛出错误
> removeRedisDataContainer(user: String): Unit -> 移除指定用户的数据容器

## 实现细节
- 构造函数接收配置部分、表名、标志列表等参数，初始化数据库和Redis连接
- 根据配置决定使用SQL数据库或本地文件数据库
- 根据配置决定是否启用Redis连接
- 使用ConcurrentHashMap存储用户数据容器，确保线程安全
- 提供方法管理用户数据容器的生命周期

## 使用场景
> 需要同时使用数据库和Redis缓存的插件
> 多服务器共享数据的场景，通过Redis实现数据同步
> 需要高性能数据读写的场景，利用Redis缓存减轻数据库压力

## 注意事项
> 配置文件必须包含Database和Redis两个部分
> Redis连接可能为null，所有Redis操作都需要进行空安全处理
> 用户标识(user)不限于玩家UUID，可以是任何唯一标识符
> 移除数据容器不会自动保存数据，需要在移除前确保数据已保存

