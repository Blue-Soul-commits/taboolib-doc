# Executor
## 基本信息 
- 类名和包路径: taboolib.common.platform.function.Executor
- 基本用途: 提供跨平台任务调度功能的顶层函数集合
- 类型: Kotlin 文件，包含顶层函数
- 所属模块: common-platform-api

## 类结构 
### 公开静态字段 
> 无公开静态字段（文件级别）

### 公开静态方法 
> startExecutor(): Unit -> 启动调度器，释放预备阶段的调度器计划
> runTask(executor: Runnable): PlatformExecutor.PlatformTask -> 执行一个简单的任务
> submit(now: Boolean = false, async: Boolean = false, delay: Long = 0, period: Long = 0, executor: PlatformExecutor.PlatformTask.() -> Unit): PlatformExecutor.PlatformTask -> 注册一个可配置的调度器任务
> submitAsync(now: Boolean = false, delay: Long = 0, period: Long = 0, executor: PlatformExecutor.PlatformTask.() -> Unit): PlatformExecutor.PlatformTask -> 注册一个异步执行的调度器任务

### 类内可被访问字段 
> 无类内可被访问字段（文件级别）

### 类方法
> 无类方法（文件级别）

## 实现细节
- 所有函数都是顶层函数，可以直接导入使用，无需通过类实例调用
- 内部通过 PlatformFactory.getService<PlatformExecutor>() 获取平台执行器服务实例
- startExecutor 函数用于启动调度器系统，释放在预备阶段注册的任务
- runTask 函数提供了执行简单任务的便捷方式，不支持延迟或周期性执行
- submit 函数是最灵活的任务提交方式，支持配置立即执行、异步执行、延迟执行和周期性执行
- submitAsync 函数是 submit 的简化版本，固定为异步执行模式
- 所有函数都返回 PlatformExecutor.PlatformTask 对象，可用于后续控制任务

## 使用场景 
> 执行延迟任务或定时任务
> 在异步线程中执行耗时操作
> 创建周期性执行的任务，如数据保存、状态更新等
> 在插件启动时初始化调度器系统

## 注意事项 
> startExecutor 函数只能执行一次且必须执行，通常由 TabooLib 在适当的时机自动调用
> 异步任务不应直接操作游戏主线程的对象，避免线程安全问题
> 时间单位为游戏 tick，1 tick 约等于 50 毫秒，20 tick 等于 1 秒
> 周期性任务（period > 0）会重复执行，直到被取消或插件被禁用