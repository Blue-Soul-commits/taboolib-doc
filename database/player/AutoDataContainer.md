# AutoDataContainer

## 基本信息
- 类名和包路径: taboolib.expansion.AutoDataContainer
- 基本用途: 数据库优先的数据容器，定期从数据库同步数据到缓存
- 类型: 普通类
- 所属模块: database-player

## 类结构

### 公开静态字段
> syncTick: Long -> 定期同步数据的时间间隔，默认为80L

### 公开静态方法
> update(): Unit -> 定期更新所有AutoDataContainer实例的数据

### 类内可被访问字段
> user: String -> 用户标识，用于区分不同用户的数据
> database: Database -> 数据库实例，用于存储和检索数据
> source: MutableMap<String, String> -> 存储用户数据的本地缓存

### 类方法
> get(key: String): String? -> 获取指定键的值
> set(key: String, value: Any): Unit -> 设置指定键的值
> keys(): Set<String> -> 获取所有键的集合
> values(): Map<String, String> -> 获取所有键值对
> size(): Int -> 获取键值对的数量
> toString(): String -> 返回对象的字符串表示
> update(): Unit -> 手动从数据库更新数据到本地缓存

## 实现细节
- 采用"数据库优先"策略，所有写操作直接写入数据库，然后更新本地缓存
- 使用定时任务定期从数据库同步数据到本地缓存
- 通过重载操作符 get 和 set 简化数据访问
- 使用 runCatching 包装更新操作，确保单个容器更新失败不影响其他容器

## 使用场景
> 需要保证数据一致性的多服务器环境
> 对数据实时性要求较高的应用
> 需要频繁读取但较少写入的数据存储

## 注意事项
> 由于定期从数据库同步数据，可能存在短暂的数据不一致
> syncTick值设置过小可能导致频繁数据库访问，增加服务器负担
> 适合读多写少的场景，写入频繁的场景可能导致性能问题
