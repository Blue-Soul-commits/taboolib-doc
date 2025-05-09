# RemoteQuestContext

## 基本信息
- 类名和包路径: taboolib.module.kether.RemoteQuestContext
- 基本用途: Kether脚本引擎的远程上下文封装，实现跨插件/容器访问和操作脚本上下文
- 类型: 类及内部类
- 所属模块: kether

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> remote: OpenContainer -> 远程容器实例，用于进行跨容器通信
> source: Any -> 远程QuestContext对象的原始引用

### 类方法
> getService(): QuestService<ScriptContext> -> 获取脚本服务实例（此方法会抛出错误）
> setExitStatus(exitStatus: ExitStatus): Unit -> 设置脚本执行的退出状态
> getExitStatus(): Optional<ExitStatus> -> 获取脚本执行的退出状态
> runActions(): CompletableFuture<Any> -> 执行脚本内的动作并返回异步结果
> getExecutor(): QuestExecutor? -> 获取脚本执行器
> terminate(): Unit -> 终止脚本执行
> rootFrame(): QuestContext.Frame -> 获取脚本执行的根帧

## 实现细节
- RemoteQuestContext继承自ScriptContext，实现了对远程脚本上下文的封装
- 在构造函数中创建RemoteQuest对象，表示远程脚本
- 大多数方法通过反射调用远程源对象的对应方法(invokeMethod)
- getService方法直接抛出错误，不支持远程获取服务实例
- 提供了两个内部类：RemoteFrame和RemoteVarTable，分别封装远程执行帧和变量表
- 使用StandardChannel通道进行远程对象的创建和操作
- 所有远程方法调用都使用remap=false，避免字段名映射问题

## 使用场景
> 跨插件访问和操作Kether脚本上下文
> 在不同ClassLoader环境下共享脚本执行状态
> 实现模块化的脚本执行系统，允许插件间共享脚本功能
> 与RemoteQuest和RemoteQuestAction配合，构建完整的远程脚本系统

## 注意事项
> 大量使用反射调用，可能存在性能开销
> getService方法不支持，直接抛出错误
> 依赖远程容器的可用性，如果远程容器不可用则操作失败
> RemoteFrame和RemoteVarTable也使用反射实现，同样存在上述问题
> 复杂对象(如ParsedAction、ExitStatus)需要特殊处理，确保跨容器正确传递
