# RemoteQuestAction

## 基本信息
- 类名和包路径: taboolib.module.kether.RemoteQuestAction
- 基本用途: Kether脚本引擎的远程动作执行类，实现跨插件/容器执行脚本动作
- 类型: 类
- 所属模块: kether

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> remote: OpenContainer -> 远程容器实例，用于进行跨容器通信
> source: Any -> 远程QuestAction对象的原始引用

### 类方法
> process(frame: QuestContext.Frame): CompletableFuture<T> -> 实现QuestAction的核心方法，处理远程动作执行

## 实现细节
- RemoteQuestAction继承自QuestAction<T>抽象类，T为动作返回值的泛型类型
- process方法实现了QuestAction的核心功能，负责执行远程动作
- 首先通过StandardChannel.REMOTE_CREATE_FLAME通道创建远程执行帧(frame)
- 然后通过反射调用远程source对象的process方法，传入创建的远程帧
- 使用pluginId作为来源标识符，确保跨容器通信的正确性
- 反射调用时使用remap=false参数，避免字段名映射问题

## 使用场景
> 跨插件执行Kether脚本动作
> 允许一个插件使用另一个插件注册的动作功能
> 在不同ClassLoader环境下共享脚本执行能力
> 与RemoteActionParser和RemoteQuest配合，构建完整的远程脚本系统

## 注意事项
> 使用反射调用远程方法，可能存在性能开销
> 依赖远程容器的可用性，如果远程容器不可用则操作失败
> 使用invokeMethod进行反射操作，需要确保远程对象结构稳定
> 远程方法调用的异常处理相对有限，可能难以诊断问题
> 远程帧的创建和使用是整个远程执行机制的关键环节
