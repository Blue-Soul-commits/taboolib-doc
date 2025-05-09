# ThrottleFunction

## 基本信息
- 类名和包路径: taboolib.common.function.ThrottleFunction
- 基本用途: 提供节流功能，限制函数在指定时间内只能执行一次
- 类型: 抽象类及其扩展函数
- 所属模块: common

## 类结构
### 公开静态字段
> allThrottleFunctions: CopyOnWriteArrayList<ThrottleFunction<*>> -> 存储所有被创建的节流函数实例

### 公开静态方法
> addThrottleFunction(throttleFunction: ThrottleFunction<*>): Unit -> 将节流函数添加到全局列表中

### 类内可被访问字段
> keyType: Class<K> -> 节流函数键的类型
> delay: Long -> 默认的节流延迟时间（毫秒）
> throttleMap: ConcurrentHashMap<K, Long> -> 存储键与上次执行时间的映射

### 类方法
> canExecute(key: K, delay: Long): Boolean -> 检查指定键是否可以执行操作
> removeKey(key: Any): Unit -> 移除指定键的节流记录
> clearAll(): Unit -> 清除所有节流记录

## 实现细节
- 使用ConcurrentHashMap存储键与上次执行时间的映射，保证线程安全
- 提供三种不同的节流函数实现：无键(Singleton)、基础(Simple)和带参数(Parameterized)
- 所有创建的节流函数实例都会被添加到全局列表中，便于统一管理
- 使用操作符重载(invoke)实现函数式调用风格

## 使用场景
> 限制UI事件处理频率，防止用户快速点击导致的重复操作
> 控制网络请求频率，避免短时间内发送过多相同请求
> 限制游戏中特定动作的执行频率，如技能释放、物品使用等

## 注意事项
> 节流函数在多线程环境下是安全的，使用了线程安全的集合类
> 默认情况下，所有创建的节流函数实例都会被添加到全局列表中，可能导致内存占用增加
> 不再需要的节流函数应该从全局列表中移除，避免内存泄漏
