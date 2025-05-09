# Listener
## 基本信息 
- 类名和包路径: taboolib.common.platform.function.Listener
- 基本用途: 提供跨平台事件监听器注册和管理的顶层函数集合
- 类型: Kotlin 文件，包含顶层函数和私有类
- 所属模块: common-platform-api

## 类结构 
### 公开静态字段 
> 无公开静态字段（文件级别）

### 公开静态方法 
> Class<*>.isListened(): Boolean -> 判断一个事件类是否在当前插件内被监听
> registerBukkitListener<T>(event: Class<T>, priority: EventPriority = EventPriority.NORMAL, ignoreCancelled: Boolean = true, func: Closeable.(T) -> Unit): ProxyListener -> 注册 Bukkit/Nukkit 平台的事件监听器
> registerBungeeListener<T>(event: Class<T>, level: Int = 0, ignoreCancelled: Boolean = false, func: Closeable.(T) -> Unit): ProxyListener -> 注册 BungeeCord 平台的事件监听器
> registerAfyBrokerListener<T>(event: Class<T>, level: Int = 0, ignoreCancelled: Boolean = false, func: Closeable.(T) -> Unit): ProxyListener -> 注册 AfyBroker 平台的事件监听器
> registerVelocityListener<T>(event: Class<T>, postOrder: PostOrder = PostOrder.NORMAL, func: Closeable.(T) -> Unit): ProxyListener -> 注册 Velocity 平台的事件监听器
> unregisterListener(proxyListener: ProxyListener): Unit -> 注销一个事件监听器

### 类内可被访问字段 
> listenEvents: CopyOnWriteArraySet<Class<*>> -> 当前插件正在监听的事件类集合（私有字段）

### 类方法
> 无类方法（文件级别）

## 实现细节
- 所有函数都是顶层函数，可以直接导入使用，无需通过类实例调用
- 内部通过 PlatformFactory.getService<PlatformListener>() 获取平台监听器服务实例
- 使用 CopyOnWriteArraySet 存储当前插件监听的事件类，支持线程安全的并发访问
- 提供了针对不同平台（Bukkit/Nukkit、BungeeCord、AfyBroker、Velocity）的事件监听器注册函数
- 所有注册函数都返回 ProxyListener 对象，可用于后续注销监听器
- 使用 CloseableListener 类包装监听器，支持通过 Closeable 接口自动注销监听器
- isListened 扩展函数可以检查事件类是否被当前插件监听，包括通过 InternalEventBus 注册的事件

## 使用场景 
> 手动注册和注销跨平台事件监听器
> 在插件运行时动态添加或移除事件监听
> 创建可自动关闭的事件监听器
> 检查特定事件是否已被监听

## 注意事项 
> 这些函数依赖于 PlatformListener 服务，确保在适当的生命周期阶段调用
> 通常不需要直接调用这些函数，而是使用 @SubscribeEvent 注解注册事件监听器
> 使用 Closeable 接口可以方便地注销监听器，避免内存泄漏
> 不同平台的事件注册参数略有不同，使用时需注意平台兼容性
