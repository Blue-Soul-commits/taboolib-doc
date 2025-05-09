# EventBus
## 基本信息 
- 类名和包路径: taboolib.common.platform.event.EventBus
- 基本用途: TabooLib 的跨平台事件总线，负责扫描和注册带有 @SubscribeEvent 注解的事件监听方法
- 类型: Kotlin 类，继承自 ClassVisitor
- 所属模块: common-platform-api

## 类结构 
### 公开静态字段 
> 无公开静态字段

### 公开静态方法 
> 无公开静态方法

### 类内可被访问字段 
> 无类内可被访问字段

### 类方法
> visit(method: ClassMethod, owner: ReflexClass): Unit -> 访问并处理带有 @SubscribeEvent 注解的方法
> registerBukkit(method: ClassMethod, optionalBind: Class<*>?, event: ClassAnnotation, obj: Any?): Unit -> 注册 Bukkit 平台的事件监听器
> registerBungee(method: ClassMethod, optionalBind: Class<*>?, event: ClassAnnotation, obj: Any?): Unit -> 注册 BungeeCord 平台的事件监听器
> registerAfyBroker(method: ClassMethod, optionalBind: Class<*>?, event: ClassAnnotation, obj: Any?): Unit -> 注册 AfyBroker 平台的事件监听器
> registerVelocity(method: ClassMethod, optionalBind: Class<*>?, event: ClassAnnotation, obj: Any?): Unit -> 注册 Velocity 平台的事件监听器
> invoke(obj: Any?, method: ClassMethod, it: Any, optional: Boolean = false): Unit -> 调用事件处理方法
> getLifeCycle(): LifeCycle -> 获取类访问器的生命周期阶段

## 实现细节
- 使用 @Awake 和 @Inject 注解标记，表示在 TabooLib 启动时自动注册
- 继承自 ClassVisitor 类，优先级设置为 -1，确保在适当的时机处理
- visit 方法扫描带有 @SubscribeEvent 注解且只有一个参数的方法
- 支持通过 bind 属性处理 OptionalEvent（可选事件），适用于可能不存在的事件类
- 支持 @Ghost 注解，用于忽略找不到事件类的警告
- 根据当前运行平台（Bukkit、BungeeCord、Velocity、AfyBroker）选择不同的注册方法
- 支持内部事件（InternalEvent）的处理，使用 InternalEventBus 进行注册
- 在 LifeCycle.ENABLE 生命周期阶段执行，确保插件完全加载后才注册事件监听器

## 使用场景 
> 自动扫描和注册带有 @SubscribeEvent 注解的事件监听方法
> 处理跨平台的事件监听机制，统一不同平台的事件处理
> 支持可选事件（OptionalEvent）的处理，增强插件的兼容性
> 作为 TabooLib 事件系统的核心组件，连接插件代码和平台事件系统

## 注意事项 
> 事件监听方法必须有且仅有一个参数，类型为要监听的事件类
> 如果事件类不存在，会输出警告，可以使用 @Ghost 注解关闭警告
> 不同平台的事件注册方式不同，EventBus 会根据当前平台选择合适的注册方法
> 事件处理的优先级和行为由 @SubscribeEvent 注解的属性控制
