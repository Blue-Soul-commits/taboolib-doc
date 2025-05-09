# Cancellable
## 基本信息
- 类名和包路径: taboolib.expansion.Cancellable
- 基本用途: 提供可取消操作的基础功能支持
- 类型: 工具类
- 所属模块: basic-submit-chain

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> cancelled: Boolean -> 表示当前操作是否已被取消，默认为 false，只读属性

### 类方法
> cancel(): Unit -> 将 cancelled 标记为 true，表示操作已被取消
> call(block: Cancellable.() -> T): T -> 执行接收者为 Cancellable 的代码块并返回结果

## 实现细节
- 作为一个开放类（open class），允许其他类继承并扩展其功能
- cancelled 字段使用 private set 修饰，确保只能通过 cancel() 方法修改
- call 方法接收一个以 Cancellable 为接收者的高阶函数，并执行该函数返回结果

## 使用场景
> 在需要支持取消操作的任务中使用，如定时任务、重复执行的操作
> 在 AsynchronousRepeatChain 和 SynchronousRepeatChain 中用于控制任务的取消状态
> 在链式调用中提供取消当前操作的能力

## 注意事项
> cancelled 字段一旦设置为 true 后无法恢复为 false
> 需要在执行的代码块中主动检查 cancelled 状态并做出相应处理

