# QuestFuture

## 基本信息
- 类名和包路径: taboolib.library.kether.QuestFuture
- 基本用途: 管理和跟踪 Kether 脚本中异步任务的执行和状态
- 类型: 泛型类
- 所属模块: minecraft-kether

## 类结构
### 类内可被访问字段
> action: ParsedAction<T> -> 保存关联的动作
> future: CompletableFuture<T> -> 保存任务执行的 Future 对象

### 公开静态方法
> complete(CompletableFuture<T> future): Consumer<T> -> 创建一个 Consumer，用于处理可能是 QuestFuture 的结果并完成指定的 future

### 类方法
> QuestFuture(ParsedAction<T> action): constructor -> 创建一个尚未运行的 QuestFuture 实例
> QuestFuture(ParsedAction<T> action, CompletableFuture<T> future): constructor -> 创建一个带有指定 future 的 QuestFuture 实例
> getAction(): ParsedAction<T> -> 获取关联的动作
> getFuture(): CompletableFuture<T> -> 获取关联的 Future 对象
> run(QuestContext.Frame frame): void -> 在指定的帧上执行动作，并保存结果的 Future 对象
> close(): void -> 关闭并清理资源，将 future 设为 null

## 实现细节
- QuestFuture 在 run 方法调用时使用帧创建一个新帧来执行动作
- 当一个动作被执行后，其结果将被存储在 future 字段中
- close 方法用于清理资源，将 future 设置为 null
- 类内部使用 Preconditions 来确保方法调用的前置条件，防止不正确的状态转换

## 使用场景
> 在 Kether 脚本变量系统中，存储异步执行的动作结果
> 在 "async" 动作中，实现异步执行其他动作的功能
> 在 "await" 动作中，等待异步任务完成并获取结果

## 注意事项
> run 方法只能在 future 为 null 时调用，否则会抛出异常
> close 方法只能在 future 不为 null 时调用，否则会抛出异常
> 在变量表中作为变量值使用时，会自动通过 join() 等待 future 完成并返回结果