# TabooLib

## 基本信息

- 类名和包路径: taboolib.common.TabooLib 
- 基本用途: TabooLib 框架的核心类，管理生命周期、唤醒类和类加载 
- 类型: 类 
- 所属模块: Common

---

## 类结构

### 公开静态字段

> isStopped: boolean -> 判断是否停止加载
> 
> currentLifeCycle: LifeCycle -> 当前生命周期阶段
> 
> awakenedClasses: ConcurrentHashMap<String, Object> -> 当前插件所有被唤醒的类

### 公开静态方法

> lifeCycle(lifeCycle: LifeCycle): void -> 执行生命周期任务
> 
> registerLifeCycleTask(lifeCycle: LifeCycle, priority: int, runnable: Runnable): void -> 推迟任务到指定生命周期下执行
> 
> isKotlinEnvironment(): boolean -> 检查当前 Kotlin 环境是否有效
> 
> isKotlinCoroutinesEnvironment(): boolean -> 检查当前 Kotlin Coroutines 环境是否有效
> 
> getCurrentLifeCycle(): LifeCycle -> 获取当前生命周期
> 
> isStopped(): boolean -> 是否停止 TabooLib 及插件加载流程
> 
> setStopped(value: boolean): void -> 停止 TabooLib 及插件加载流程
> 
> getAwakenedClasses(): Map<String, Object> -> 获取当前插件所有被唤醒的类
> 
> getClass(name: String): Class<?> -> 获取类（为适配 Paper 特殊处理）
> 
> getClass(name: String, initialize: boolean): Class<?> -> 获取类（可指定是否初始化）
> 
> getClass(name: String, initialize: boolean, classLoader: ClassLoader): Class<?> -> 获取类（可指定类加载器）
> 
> setClassFinder(classFinder: ClassFinder): void -> 设置类查找器
> 
> getClassFinder(): ClassFinder -> 获取类查找器
> 
> execution(task: Runnable): long -> 执行给定的代码块，并返回所用时间（以毫秒为单位）

### 类内可被访问字段

> classFinder: ClassFinder -> 类查找器
> 
> lifeCycleTask: ConcurrentHashMap<LifeCycle, List<LifeCycleTask>> -> 生命周期任务

### 类方法

> 无实例方法

---

## 实现细节

- 提供了生命周期管理机制，可以在特定生命周期阶段执行注册的任务

- 提供类查找功能，专门处理 paper 1.20.6+ 对 Class.forName 调用的接管

- 包含内部类 ClassFinder 作为类查找的抽象接口

--- 

## 使用场景

> 在插件开发过程中管理不同阶段的初始化
> 
> 检查运行环境是否满足要求（kotlin环境检查）
> 
> 安全的获取类，避免Paper平台兼容性的问题

## 注意事项

> 外部模块需要通过 Taboolib.getClass() 获取类，而不是直接使用 Class.forName()
> 
> 生命周期任务按照优先级排序执行
