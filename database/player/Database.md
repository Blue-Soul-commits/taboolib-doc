# Database

## 基本信息
- 类名和包路径: taboolib.expansion.Database
- 基本用途: 提供用户数据的存储和检索功能，支持键值对形式的数据管理
- 类型: 普通类
- 所属模块: database-player

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> type: Type -> 数据库类型，决定了底层数据库的实现方式
> dataSource: DataSource -> 数据源，用于与数据库建立连接

### 类方法
> get(user: String): MutableMap<String, String> -> 获取指定用户的所有键值对数据
> get(user: String, key: String): String? -> 获取指定用户的特定键的值
> set(user: String, key: String, data: String): Unit -> 设置指定用户特定键的值
> getValue(user: String, key: String): String? -> 查询指定用户特定键的值
> getUserList(key: String, value: String): List<String> -> 获取所有满足特定键值对的用户列表
> getListByKey(key: String): MutableMap<String, String> -> 根据键获取所有用户的对应值
> getLikeKeyList(user: String, key: String): MutableMap<String, String> -> 模糊查询用户数据，返回键以指定前缀开头的所有数据
> remove(user: String, key: String): Unit -> 删除指定用户的特定键值对

## 实现细节
- 使用 Type 接口来抽象不同类型的数据库实现（如SQL、SQLite等）
- 通过重载操作符 get 和 set 来简化数据访问
- 使用 ConcurrentHashMap 确保线程安全
- 在初始化时自动创建数据表
- 空值处理：当设置空值时自动转为删除操作

## 使用场景
> 玩家数据持久化存储，如游戏进度、设置、成就等
> 跨服务器数据同步，通过共享数据库实现
> 临时数据缓存，用于减少数据库查询次数

## 注意事项
> 大量数据操作时应考虑性能影响，可能需要批量操作或异步处理
> 数据库连接应适时关闭以释放资源
> 对于频繁访问的数据，考虑使用本地缓存减少数据库查询
