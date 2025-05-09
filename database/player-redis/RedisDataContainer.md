# RedisDataContainer

## 基本信息
- 类名和包路径: taboolib.expansion.RedisDataContainer
- 基本用途: 提供Redis缓存与数据库交互的容器，实现数据的读写和缓存管理
- 类型: 数据容器类
- 所属模块: database-player-redis

## 类结构

### 公开静态字段
> REDIS_SECONDS: Long -> 缓存过期时间，默认为1800秒（30分钟）
> REDIS_TIMEOUT: TimeUnit -> 缓存过期时间单位，默认为TimeUnit.SECONDS

### 公开静态方法
> 无

### 类内可被访问字段
> user: String -> 用户标识，用于数据库索引
> database: Database -> 数据库实例，用于持久化存储
> redis: RedisDatabaseHandler -> Redis数据管理器，用于缓存操作

### 类方法
> set(key: String, value: Any): Unit -> 设置指定键的值并立即保存，同时删除Redis缓存
> setDelayed(key: String, value: Any, delay: Long = 3L, timeUnit: TimeUnit = TimeUnit.SECONDS): Unit -> 设置指定键的值，并在指定延迟后删除（不进入数据库）
> get(key: String): String? -> 获取指定键的值，优先从缓存中取出，若无则从数据库获取并设置到缓存
> toString(): String -> 返回对象的字符串表示

## 实现细节
- 读取数据时优先从Redis缓存获取，若缓存不存在则从数据库读取并设置到缓存中
- 写入数据时会先删除Redis缓存，然后写入数据库
- 支持设置临时数据，这些数据只存在于Redis中，不会写入数据库，并在指定时间后自动删除
- 缓存过期时间可通过静态变量全局配置

## 使用场景
> 需要频繁读取但较少写入的数据，如玩家配置、权限等
> 需要临时存储的数据，如登录状态、验证码等
> 多服务器共享数据的场景，通过Redis实现数据同步

## 注意事项
> Redis连接可能为null，所有Redis操作都需要进行空安全处理
> 写入操作会立即删除缓存，确保数据一致性
> 读取操作会自动更新缓存，并设置过期时间
> 临时数据(setDelayed)不会写入数据库，仅存在于Redis中