# PlatformFactory
## 基本信息 
- 类名和包路径: taboolib.common.platform.PlatformFactory
- 基本用途: TabooLib 的平台抽象工厂，负责管理跨平台服务、API 实例和类的自动唤醒
- 类型: Kotlin 单例对象
- 所属模块: common-platform-api

## 类结构 
### 公开静态字段 
> awokenMap: ConcurrentHashMap<String, Any> -> 存储已被唤醒的类实例，键为类的全限定名
> serviceMap: ConcurrentHashMap<String, Any> -> 存储已注册的跨平台服务，键为服务接口的全限定名

### 公开静态方法 
> getAPI<T>(name: String): T -> 获取已被唤醒的 API 实例，如果不存在则抛出异常
> getService<T>(name: String): T -> 获取已注册的跨平台服务，如果不存在则抛出异常
> getAPI<T>(): T -> 获取已被唤醒的 API 实例，使用泛型类型作为键
> getAPIOrNull<T>(): T? -> 获取已被唤醒的 API 实例，如果不存在则返回 null
> getService<T>(): T -> 获取已注册的跨平台服务，使用泛型类型作为键
> getServiceOrNull<T>(): T? -> 获取已注册的跨平台服务，如果不存在则返回 null
> registerAPI<T: Any>(instance: T): Unit -> 注册 API 实例
> registerService<T: Any>(instance: T): Unit -> 注册跨平台服务

### 类内可被访问字段 
> 无类内可被访问字段

### 类方法
> init(): Unit -> 初始化平台工厂，注册生命周期任务
> injectByCache(bytes: ByteArray, time: Long): Unit -> 从二进制缓存中注入类和服务
> inject(includedClasses: Set<ReflexClass>, time: Long): Unit -> 扫描并注入类和服务

## 实现细节
- 使用单例模式实现，作为 TabooLib 平台抽象层的核心组件
- 在 CONST 生命周期阶段初始化，注册 ClassVisitorAwake 处理器
- 支持从二进制缓存中快速恢复类和服务的注册状态，提高启动性能
- 自动识别并处理带有 @Awake 注解的类，创建实例并存储在 awokenMap 中
- 自动识别并处理实现了带有 @PlatformService 注解的接口的类，注册为跨平台服务
- 在 DISABLE 生命周期阶段，自动释放实现了 Releasable 接口的实例
- 提供泛型和非泛型两种方式获取 API 实例和服务

## 使用场景 
> 获取跨平台服务实例，实现平台无关的功能调用
> 获取已注册的 API 实例，访问全局功能
> 注册自定义 API 或服务，扩展 TabooLib 功能
> 实现插件在不同平台上的统一接口

## 注意事项 
> 获取不存在的 API 或服务时，getAPI 和 getService 方法会抛出异常
> 对于可能不存在的 API 或服务，应使用 getAPIOrNull 和 getServiceOrNull 方法
> 平台服务的注册主要通过 @PlatformService 注解和 @Awake 注解自动完成
> 在调试模式下，会输出详细的初始化信息，包括唤醒类数量、注入数量和服务列表