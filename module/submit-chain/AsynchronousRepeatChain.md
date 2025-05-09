# AsynchronousRepeatChain
## 基本信息
- 类名和包路径: taboolib.expansion.AsynchronousRepeatChain
- 基本用途: 提供异步重复执行任务的链式调用功能，直到任务被取消为止
- 类型: 协程支持类
- 所属模块: basic-submit-chain

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> block: Cancellable.() -> T -> 可取消的代码块，返回类型为泛型T
> period: Long -> 任务重复执行的周期（单位：tick）
> now: Boolean -> 是否立即执行任务
> delay: Long -> 任务首次执行的延迟时间（单位：tick）

### 类方法
> execute(): T -> 执行重复任务直到被取消，并返回最终结果

## 实现细节
- 实现了 RepeatChainable<T> 接口，提供可重复执行的链式调用功能
- 使用 suspendCoroutine 挂起当前协程，直到任务被取消
- 通过 taboolib.common.platform.function.submit 函数创建异步重复执行的任务
- 使用 Cancellable 类来控制任务的取消状态
- 当 Cancellable.cancelled 为 true 时，任务会被取消并恢复协程执行

## 使用场景
> 在 Chain 类中通过 async 方法调用，用于创建异步重复执行的任务
> 适用于需要定期执行直到满足某个条件的异步任务，如倒计时、轮询等

## 注意事项
> 必须在协程上下文中使用，因为 execute() 方法是 suspend 函数
> 任务会一直重复执行，直到在代码块中调用 cancel() 方法
> 任务取消后会返回最后一次执行的结果

