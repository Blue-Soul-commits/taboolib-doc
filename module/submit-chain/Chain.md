# Chain
## 基本信息
- 类名和包路径: taboolib.expansion.Chain
- 基本用途: 提供基于 Kotlin 协程的链式任务调度框架
- 类型: 协程调度框架
- 所属模块: basic-submit-chain

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> chain(type: DispatcherType = ASYNC, block: suspend Chain<R>.() -> R): CompletableFuture<R> -> 创建并运行一个链式任务，返回 CompletableFuture
> submitChain(type: DispatcherType = ASYNC, block: suspend Chain<R>.() -> R): CompletableFuture<R> -> chain 函数的别名

### 类内可被访问字段
> chain: suspend Chain<R>.() -> R -> 链式任务的执行代码块

### 类方法
> async(block: () -> T): T -> 在异步调度器上执行代码块
> sync(block: () -> T): T -> 在同步调度器上执行代码块
> wait(value: Long, type: DurationType) -> 等待指定时间
> sync(period: Long, now: Boolean = false, delay: Long = 0L, block: Cancellable.() -> T): T -> 创建同步重复执行的任务
> async(period: Long, now: Boolean = false, delay: Long = 0L, block: Cancellable.() -> T): T -> 创建异步重复执行的任务
> run(type: DispatcherType): CompletableFuture<R> -> 在指定调度器类型上运行链式任务

## 实现细节
- 基于 Kotlin 协程实现，提供同步和异步两种调度器
- SyncDispatcher 和 AsyncDispatcher 分别对应 Minecraft 的主线程和异步线程
- 通过 withContext 切换协程上下文，实现线程调度
- 支持任务等待、单次执行和重复执行等多种调度方式
- 使用 CompletableFuture 作为异步结果的返回值，方便与 Java 代码集成

## 使用场景
> 需要在 Minecraft 中进行复杂的异步操作时
> 需要在主线程和异步线程之间切换执行代码
> 需要定时或重复执行任务，并在满足条件时取消
> 需要等待特定时间后执行代码

## 注意事项
> 在 chain 代码块中的代码是在协程上下文中执行的，可以使用 suspend 函数
> 默认使用异步调度器，如需在主线程执行，需要显式指定 DispatcherType.SYNC
> 时间单位可以是 Minecraft tick (1 tick = 50ms) 或毫秒
> 重复执行的任务需要手动调用 cancel() 方法才会停止

