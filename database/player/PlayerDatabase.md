# PlayerDatabase

## 基本信息
- 类名和包路径: taboolib.expansion.PlayerDatabase
- 基本用途: 玩家数据库抽象类，用于管理玩家数据的存储和检索
- 类型: 抽象类
- 所属模块: database-player

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> database: Database? -> 私有字段，数据库实例
> dataContainer: ConcurrentHashMap<UUID, DataContainer> -> 私有字段，存储玩家UUID与数据容器的映射

### 类方法
> setupSQLDatabase(conf: ConfigurationSection, table: String, flags: List<String>, clearFlags: Boolean, ssl: String?): Unit -> 设置基于SQL的数据库配置
> setupSQLiteDatabase(file: File): Unit -> 设置基于SQLite的数据库配置
> getDataContainer(player: ProxyPlayer): DataContainer -> 获取玩家的数据容器
> setupDataContainer(player: ProxyPlayer, usernameMode: Boolean): Unit -> 设置玩家的数据容器，可选择使用玩家名作为用户名
> setupDataContainer(player: ProxyPlayer): Unit -> 设置玩家对应的数据容器，使用UUID作为用户名
> setupDataContainer(uuid: UUID): Unit -> 设置UUID对应的数据容器
> getDataContainer(uuid: UUID): DataContainer -> 获取UUID对应的数据容器
> releaseDataContainer(uuid: UUID): Unit -> 释放UUID对应的数据容器
> releaseDataContainer(player: ProxyPlayer): Unit -> 释放玩家对应的数据容器
> init(config: ConfigurationSection, table: String, sqlitePath: String, configDatabase: String): Unit -> 初始化数据库配置

## 实现细节
- 该类是一个抽象类，需要被继承使用
- 内部维护一个数据库实例和一个并发哈希映射，用于存储玩家UUID与数据容器的映射
- 支持SQL和SQLite两种数据库类型
- 提供了多种方法来设置和获取玩家数据容器
- 初始化方法会根据配置决定使用SQL还是SQLite数据库

## 使用场景
> 需要为玩家存储持久化数据的插件
> 需要在不同服务器之间共享玩家数据的网络
> 需要在插件重启后恢复玩家数据的场景

## 注意事项
> 使用前必须先初始化数据库，否则会出现空指针异常
> 玩家数据容器在不需要时应该被释放，以避免内存泄漏
> 在多线程环境下使用时需要注意线程安全问题
> 初始化失败时会打印异常堆栈但不会抛出异常，需要自行检查初始化是否成功
