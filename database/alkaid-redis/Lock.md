# Lock
## 基本信息
- 类名和包路径: taboolib.expansion.lock.Lock
- 基本用途: Redis分布式锁实现
- 类型: 普通类
- 所属模块: database-alkaid-redis

## 类结构
### 类内可被访问字段
> connection: IRedisConnection -> Redis连接
> lockName: String -> 锁名称，通过getter添加前缀
> internalLockLeaseTime: Long -> 锁租约时间（秒）
> start: Boolean -> 锁是否已启动
> watchDog: Boolean -> 看门狗状态标志

### 类方法
> tryLock(): Boolean -> 尝试获取锁
> unlock(): Unit -> 释放锁
> extended(): Unit -> 延长锁的有效时间（看门狗机制）
> prefixName(prefix: String, name: String): String -> 为锁名称添加前缀

### 伴生对象
> LOCKED: String -> 锁定状态的值常量，值为"TRUE"

## 实现细节
- 使用Redis的SETNX命令实现分布式锁
- 使用Lua脚本确保操作的原子性
- 实现了看门狗机制，自动延长锁的有效期
- 锁名称使用前缀格式化，确保命名空间隔离

## 锁的工作流程
1. **获取锁**：
   - 使用SETNX命令尝试设置锁键
   - 如果成功，设置过期时间并启动看门狗
   - 如果失败，表示锁已被其他客户端持有

2. **看门狗机制**：
   - 当锁获取成功后，启动定期任务
   - 每20个时间单位检查一次锁状态
   - 如果锁仍然存在且值匹配，延长锁的过期时间
   - 确保长时间操作不会因为锁过期而失败

3. **释放锁**：
   - 使用Lua脚本检查锁是否存在且值匹配
   - 只有当前持有者才能释放锁
   - 防止错误释放其他客户端持有的锁

## 使用场景
> 分布式系统中的资源同步
> 防止多个服务实例同时执行相同任务
> 实现分布式系统中的互斥访问

## 注意事项
> 锁的租约时间默认为30秒，可以根据需要调整
> 看门狗机制会自动延长锁的有效期，但如果客户端崩溃，锁最终会过期
> 使用try-catch块处理异常，确保锁操作的稳定性
