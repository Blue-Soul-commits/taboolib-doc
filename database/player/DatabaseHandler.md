# DatabaseHandler

## 基本信息
- 类名和包路径: taboolib.expansion.DatabaseHandler (文件名)
- 基本用途: 提供玩家数据库操作的工具函数和全局变量
- 类型: 工具类文件（包含顶层函数和变量）
- 所属模块: database-player

## 类结构

### 公开静态字段
> playerDatabase: Database? -> 玩家数据库实例，初始为null，在设置数据库连接后被赋值
> playerDataContainer: ConcurrentHashMap<UUID, DataContainer> -> 玩家数据容器映射，以UUID为键
> playerAutoDataContainer: ConcurrentHashMap<UUID, AutoDataContainer> -> 玩家自动数据容器映射，以UUID为键

### 公开静态方法
> setupPlayerDatabase(conf: ConfigurationSection, table: String, flags: List<String>, clearFlags: Boolean, ssl: String?): Unit -> 设置玩家SQL数据库
> setupPlayerDatabase(host: String, port: Int, user: String, password: String, database: String, table: String, flags: List<String>, clearFlags: Boolean, ssl: String?): Unit -> 设置玩家SQL数据库（直接参数）
> buildPlayerDatabase(conf: ConfigurationSection, table: String, flags: List<String>, clearFlags: Boolean, ssl: String?): Database -> 构建玩家SQL数据库
> setupPlayerDatabase(file: File): Unit -> 设置玩家SQLite数据库
> setupPlayerDatabase(file: File, tableName: String): Unit -> 设置玩家SQLite数据库（指定表名）
> buildPlayerDatabase(file: File, table: String): Database -> 构建玩家SQLite数据库

### 扩展函数
> ProxyPlayer.getDataContainer(): DataContainer -> 获取玩家的数据容器
> ProxyPlayer.setupDataContainer(usernameMode: Boolean): Unit -> 为玩家设置数据容器
> UUID.setupPlayerDataContainer(): Unit -> 为UUID设置玩家数据容器
> UUID.getPlayerDataContainer(): DataContainer -> 获取UUID对应的玩家数据容器
> UUID.releasePlayerDataContainer(): Unit -> 释放UUID对应的玩家数据容器
> ProxyPlayer.releaseDataContainer(): Unit -> 释放玩家的数据容器
> UUID.getAutoDataContainer(): AutoDataContainer -> 获取UUID对应的自动数据容器
> UUID.releaseAutoDataContainer(): Unit -> 释放UUID对应的自动数据容器

## 实现细节
- 提供了全局变量来存储数据库实例和玩家数据容器
- 支持SQL和SQLite两种数据库类型的设置和构建
- 提供了一系列扩展函数，简化对玩家数据的操作
- 使用ConcurrentHashMap确保线程安全
- 区分了"设置"和"构建"函数，前者会修改全局变量，后者只返回实例

## 使用场景
> 需要快速设置和使用玩家数据库的插件
> 需要在不同组件间共享玩家数据的场景
> 需要同时处理缓存优先和数据库优先两种数据容器的场景

## 注意事项
> 使用前必须先设置数据库，否则会出现空指针异常
> 玩家数据容器在不需要时应该被释放，以避免内存泄漏
> 全局变量可能导致不同插件之间的冲突，使用时需谨慎
> 自动数据容器和普通数据容器的行为不同，前者是数据库优先，后者是缓存优先
