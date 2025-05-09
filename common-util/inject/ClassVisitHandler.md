# ClassVisitorHandler

## 基本信息
- 类名和包路径: taboolib.common.inject.ClassVisitorHandler
- 基本用途: 管理和执行类访问器(ClassVisitor)的核心处理器，负责依赖注入和类扫描
- 类型: 工具类(Utility Class)
- 所属模块: TabooLib 注入模块

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> getClasses(): Set<ReflexClass> -> 获取能够被 ClassVisitor 访问到的所有类
> checkPlatform(cls: ReflexClass): boolean -> 检查指定类是否允许在当前平台运行
> register(classVisitor: ClassVisitor): void -> 注册依赖注入接口
> injectAll(clazz: ReflexClass): void -> 对给定类进行依赖注入
> injectAll(lifeCycle: LifeCycle): void -> 根据生命周期对所有类进行依赖注入
> inject(clazz: ReflexClass, group: VisitorGroup, lifeCycle: LifeCycle): void -> 对给定类进行依赖注入

### 类内可被访问字段
> propertyMap: NavigableMap<Byte, VisitorGroup> -> 按优先级存储访问器组的映射
> classes: Set<ReflexClass> -> 缓存的可访问类集合

### 类方法
> init(): void -> 初始化函数
> visitStart(clazz: ReflexClass, group: VisitorGroup, lifeCycle: LifeCycle): void -> 执行类开始访问
> visitField(clazz: ReflexClass, group: VisitorGroup, lifeCycle: LifeCycle): void -> 执行字段访问
> visitMethod(clazz: ReflexClass, group: VisitorGroup, lifeCycle: LifeCycle): void -> 执行方法访问
> visitEnd(clazz: ReflexClass, group: VisitorGroup, lifeCycle: LifeCycle): void -> 执行类结束访问
> isAnonymousInnerClass(name: String): boolean -> 判断是否为匿名内部类
> isProjectClass(name: String): boolean -> 判断是否为本项目的类
> isTabooLibClass(name: String): boolean -> 判断是否为 TabooLib 类
> isLibraryClass(name: String): boolean -> 判断是否为可能的第三方库

## 实现细节
- 使用 NavigableMap 按优先级存储访问器组，确保访问器按优先级顺序执行
- 使用懒加载方式初始化类集合，只在首次调用 getClasses() 时执行扫描
- 在初始化时为每个生命周期注册任务，确保在适当的时机执行类访问
- 提供类过滤机制，排除匿名内部类、第三方库类和不符合平台要求的类
- 支持通过 Ghost 注解完全跳过类的注入过程
- 支持通过 SkipTo 注解控制类在特定生命周期前不执行注入
- 使用异常捕获和包装机制，确保一个访问器的失败不会影响其他访问器的执行

## 使用场景
> 实现依赖注入框架
> 在应用启动过程中扫描和处理类
> 根据生命周期执行不同阶段的类处理
> 实现基于注解的功能扩展

## 注意事项
> 类扫描过程可能较为耗时，但结果会被缓存
> 访问器按优先级排序，优先级高的先执行
> 异常会被捕获并包装为 ClassVisitException，不会中断整个处理流程
> 只有带有 @Inject 注解的 TabooLib 类才会被处理
> 带有 @PlatformSide 注解的类只会在指定平台上被处理
