# ScriptSchedulerExecutor

## 基本信息
- 类名和包路径: taboolib.module.kether.ScriptSchedulerExecutor
- 基本用途: Kether脚本引擎的调度执行器，确保任务在主线程上执行
- 类型: 单例对象(object)
- 所属模块: kether

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> 无

### 类方法
> execute(command: Runnable): Unit -> 实现Executor接口的方法，执行给定的任务

## 实现细节
- ScriptSchedulerExecutor实现了Java标准库的Executor接口
- 在execute方法中，首先检查当前线程是否为主线程(isPrimaryThread)
- 如果当前已经在主线程中，则直接执行任务(command.run())
- 如果不在主线程中，则使用TabooLib的submit函数将任务提交到主线程执行
- 通过这种方式确保所有脚本任务都在主线程上执行，避免并发问题

## 使用场景
> 作为Kether脚本引擎的默认执行器
> 确保脚本动作在主线程上执行，避免线程安全问题
> 与ScriptContext配合，为脚本执行提供正确的线程环境
> 处理异步操作与主线程操作的协调

## 注意事项
> 所有任务最终都会在主线程上执行，可能导致主线程负载增加
> 不适合执行长时间运行的阻塞操作，可能影响服务器性能
> 依赖于TabooLib的平台抽象层提供的isPrimaryThread和submit函数
> 作为单例对象使用，被所有脚本上下文共享