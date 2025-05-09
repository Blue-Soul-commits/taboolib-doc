# RepeatChainable
## 基本信息
- 类名和包路径: taboolib.expansion.RepeatChainable
- 基本用途: 定义可重复执行任务的接口规范
- 类型: 接口
- 所属模块: basic-submit-chain

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> block: Cancellable.() -> T -> 可取消的代码块，返回类型为泛型T

### 类方法
> execute(): T -> 挂起函数，执行重复任务并返回结果

## 实现细节
- 泛型接口，支持任意返回类型T
- 定义了可重复执行任务的基本规范
- 要求实现类提供 execute() 挂起函数的具体实现
- 使用 Cancellable 作为代码块的接收者，提供取消操作的能力

## 使用场景
> 作为 SynchronousRepeatChain 和 AsynchronousRepeatChain 的共同接口
> 在 Chain 类中用于创建可重复执行的任务
> 适用于需要定期执行直到满足某个条件的任务场景

## 注意事项
> 实现类需要处理任务的重复执行逻辑
> 实现类需要处理任务的取消逻辑
> execute() 方法是挂起函数，必须在协程上下文中调用

