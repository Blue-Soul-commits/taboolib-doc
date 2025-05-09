# DataContainer

## 基本信息
- 类名和包路径: taboolib.expansion.DataContainer
- 基本用途: 缓存优先的数据容器，用于缓存数据并在一定时间后写入数据库
- 类型: 普通类
- 所属模块: database-player

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> checkUpdate(): Unit -> 定期检查并更新所有DataContainer实例中需要保存的数据

### 类内可被访问字段
> user: String -> 用户标识，用于区分不同用户的数据
> database: Database -> 数据库实例，用于存储和检索数据
> source: MutableMap<String, String> -> 存储用户数据的本地缓存
> updateMap: ConcurrentHashMap<String, Long> -> 存储需要更新的键值对及其更新时间

### 类方法
> set(key: String, value: Any): Unit -> 设置指定键的值并立即保存
> forcedSet(targetUser: String, key: String, value: Any, sync: Boolean): Unit -> 穿透缓存直接写入数据库
> setDelayed(key: String, value: Any, delay: Long, timeUnit: TimeUnit): Unit -> 设置指定键的值，并在指定延迟后更新
> get(key: String): String? -> 获取指定键的值
> keys(): Set<String> -> 获取所有键的集合
> values(): Map<String, String> -> 获取所有键值对
> size(): Int -> 获取键值对的数量
> save(key: String): Unit -> 保存指定键的值到数据库
> delete(key: String): Unit -> 从数据库删除指定的键
> checkUpdate(): Unit -> 检查并更新需要保存的键值对
> toString(): String -> 返回对象的字符串表示

## 实现细节
- 采用"缓存优先"策略，所有读写操作优先在本地缓存进行
- 写操作可以选择立即保存或延迟保存到数据库
- 使用ConcurrentHashMap存储需要延迟更新的键值对及其更新时间
- 通过定时任务定期检查并将需要更新的数据写入数据库
- 支持穿透缓存直接操作数据库的功能
- 所有数据库操作都在异步线程中执行，避免阻塞主线程

## 使用场景
> 需要频繁读写但对数据实时性要求不高的应用
> 游戏中玩家数据的临时存储，如经验值、金币等
> 需要减轻数据库负担的高并发环境
> 需要批量延迟写入数据库的场景

## 注意事项
> 由于采用缓存优先策略，数据库中的数据变更不会自动同步到缓存
> 服务器意外关闭可能导致未保存的数据丢失
> 多服务器环境下可能存在数据不一致问题，需要额外的同步机制
> forcedSet方法在sync=true时要求targetUser为有效的UUID字符串
