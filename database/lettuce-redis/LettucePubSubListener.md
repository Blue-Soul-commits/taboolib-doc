# LettucePubSubListener

## 基本信息
- 类名和包路径: taboolib.expansion.LettucePubSubListener
- 基本用途: 提供Redis发布订阅(Pub/Sub)事件的监听器，支持DSL风格配置
- 类型: 类(Class)和顶层函数(Top-level function)
- 所属模块: database-lettuce-redis

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> pubSubListener(action: LettucePubSubListener.() -> Unit): LettucePubSubListener -> 创建并配置一个Redis发布订阅监听器的顶层函数

### 类内可被访问字段
> onMessage: ((channel: String, message: String) -> Unit) -> 处理普通消息的回调函数
> onMessagePattern: ((pattern: String, channel: String, message: String) -> Unit) -> 处理模式匹配消息的回调函数
> onSubscribed: ((channel: String, count: Long) -> Unit) -> 处理频道订阅成功的回调函数
> onPSubscribed: ((pattern: String, count: Long) -> Unit) -> 处理模式订阅成功的回调函数
> onUnsubscribed: ((channel: String, count: Long) -> Unit) -> 处理取消频道订阅的回调函数
> onPunsubscribed: ((pattern: String, count: Long) -> Unit) -> 处理取消模式订阅的回调函数

### 类方法
> message(channel: String, message: String): Unit -> 处理普通消息的方法，会调用onMessage回调
> message(pattern: String, channel: String, message: String): Unit -> 处理模式匹配消息的方法，会调用onMessagePattern回调
> subscribed(channel: String, count: Long): Unit -> 处理频道订阅成功的方法，会调用onSubscribed回调
> psubscribed(pattern: String?, count: Long): Unit -> 处理模式订阅成功的方法，会调用onPSubscribed回调
> unsubscribed(channel: String, count: Long): Unit -> 处理取消频道订阅的方法，会调用onUnsubscribed回调
> punsubscribed(pattern: String, count: Long): Unit -> 处理取消模式订阅的方法，会调用onPunsubscribed回调

## 实现细节
- 实现了Lettuce的RedisPubSubListener接口，用于处理Redis的发布订阅事件
- 提供了DSL风格的API，使用Kotlin的函数扩展特性简化配置
- 所有回调函数都有默认的空实现，允许只配置关心的事件
- 在psubscribed方法中对pattern参数进行了非空断言，确保回调函数接收到非空值

## 使用场景
> 需要监听Redis发布订阅事件的场景
> 需要实现基于Redis的消息队列或实时通知系统
> 需要在分布式系统中实现跨服务通信

## 注意事项
> 回调函数在Redis客户端的I/O线程中执行，应避免长时间阻塞
> 如需执行耗时操作，应在回调中将任务提交到单独的线程池
> 在psubscribed方法中对pattern参数进行了非空断言，如果Redis服务器返回null可能会抛出异常