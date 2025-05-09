# MultipleHandler

## 基本信息
- 类名和包路径: taboolib.expansion.MultipleHandler
- 基本用途: 多表处理器，用于管理多个数据表和数据容器
- 类型: 工具类
- 所属模块: database-player

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> conf: ConfigurationSection -> 配置部分，用于初始化数据库
> database: Database -> 数据库实例
> databaseContainer: ConcurrentHashMap<String, DataContainer> -> 存储数据容器的并发哈希映射
> autoDataContainer: ConcurrentHashMap<String, AutoDataContainer> -> 存储自动数据容器的并发哈希映射
> taskFlag: Boolean -> 私有字段，用于控制同步任务的终止

### 类方法
> stopSync(): Unit -> 停止同步AutoDataContainer
> restartSync(): Unit -> 重新启动同步AutoDataContainer
> setupDataContainer(user: String): DataContainer -> 初始化并返回指定用户的数据容器
> getDataContainer(user: String): DataContainer -> 获取指定用户的数据容器
> getAutoDataContainer(user: String): AutoDataContainer -> 获取指定用户的数据库优先数据容器
> removeDataContainer(user: String): Unit -> 移除指定用户的数据容器
> removeAutoDataContainer(user: String): Unit -> 移除指定用户的数据库优先数据容器
> removeContainer(user: String): Unit -> 移除指定用户的两种类型容器
> updateAutoDataContainer(): Unit -> 更新所有AutoDataContainer

## 实现细节
- 构造函数接受多个参数，包括配置部分、表名、标志列表等，用于初始化数据库
- 根据配置决定使用SQL数据库或SQLite数据库
- 支持自动挂钩玩家的登录与退出事件，用于自动创建与销毁数据容器
- 使用异步任务定期更新自动数据容器
- 提供方法控制同步任务的启停

## 使用场景
> 需要管理多个数据表和数据容器的插件
> 需要同时处理缓存优先和数据库优先两种数据容器的场景
> 需要自动处理玩家数据加载和卸载的场景

## 注意事项
> 使用autoHook=true时，会自动注册到MultipleHandlerListener中处理玩家事件
> 数据容器的键不一定是玩家的UUID，可以是任何字符串
> 停止同步后需要手动调用restartSync重新启动同步
