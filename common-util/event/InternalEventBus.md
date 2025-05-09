# InternalEventBus

## 基本信息
- 类名和包路径: taboolib.common.event.InternalEventBus
- 基本用途: 提供一个内部事件总线，用于事件的注册、监听和触发
- 类型: 接口(Interface)
- 所属模块: TabooLib 公共模块

## 类结构

### 公开静态字段
> impl: InternalEventBus -> 事件总线的默认实现

### 公开静态方法
> isListening(cls: Class<*>): Boolean -> 判断一个事件类型是否有监听器
> call(event: T): Unit -> 触发一个事件
> listen(cls: Class<T>, priority: Int = 0, ignoreCancelled: Boolean = false, listener: (event: T) -> Unit): InternalListener -> 注册一个事件监听器
> listen<reified T : InternalEvent>(priority: Int = 0, ignoreCancelled: Boolean = false, listener: (event: T) -> Unit): InternalListener -> 使用泛型注册事件监听器

### 类内可被访问字段
> 无

### 类方法
> isListening(cls: Class<*>): Boolean -> 判断一个事件类型是否有监听器
> call(event: T): Unit -> 触发一个事件
> listen(cls: Class<T>, priority: Int, ignoreCancelled: Boolean, listener: (event: T) -> Unit): InternalListener -> 注册一个事件监听器

## 实现细节
- 使用 ConcurrentHashMap 存储已注册的监听器，确保线程安全
- 使用 ConcurrentSkipListMap 按优先级排序监听器
- 使用 CopyOnWriteArrayList 存储相同优先级的监听器，支持并发修改
- 默认实现通过匿名对象提供，可以被替换为自定义实现
- 支持可取消事件(CancelableInternalEvent)，可以设置监听器是否忽略已取消的事件
- 监听器注册后返回 InternalListener 接口实例，可用于取消监听

## 使用场景
> 在插件内部实现事件系统，用于模块间通信
> 在不依赖外部平台的情况下实现事件驱动架构
> 实现轻量级的观察者模式

## 注意事项
> 事件监听器的优先级默认为0，数值越大优先级越高
> 可以通过设置 ignoreCancelled 参数决定监听器是否处理已取消的事件
> 使用泛型版本的 listen 方法可以避免显式指定事件类型
> 监听器注册后需要保存返回的 InternalListener 对象，以便后续取消监听
