# ScriptAction

## 基本信息
- 类名和包路径: taboolib.module.kether.ScriptAction
- 基本用途: Kether脚本引擎中的基础动作抽象类，为TabooLib中的Kether脚本动作提供统一接口
- 类型: 抽象类
- 所属模块: kether

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> 无

### 类方法
> process(frame: ScriptFrame): CompletableFuture<T> -> 实现QuestAction的process方法，内部调用run方法
> run(frame: ScriptFrame): CompletableFuture<T> -> 抽象方法，由子类实现以定义动作的具体逻辑
> toString(): String -> 重写Object的toString方法，返回动作类的简单类名

## 实现细节
- ScriptAction是一个泛型抽象类，继承自QuestAction<T>，T表示动作的返回值类型
- 实现了QuestAction的process方法，将frame转换为ScriptFrame类型并调用抽象方法run
- 抽象方法run定义了动作的核心逻辑，需要子类实现
- 所有动作执行都返回CompletableFuture，支持异步操作
- 提供了统一的toString实现，便于调试和日志记录

## 使用场景
> 作为TabooLib中所有Kether脚本动作的基类
> 提供统一的接口，使不同动作实现保持一致的结构
> 简化异步动作的实现，通过CompletableFuture支持复杂的异步流程
> 与ScriptFrame配合使用，提供更多针对TabooLib环境的扩展功能

## 注意事项
> 所有子类必须实现run方法，定义动作的具体执行逻辑
> 动作执行是异步的，返回CompletableFuture而非直接返回结果
> process方法将library.kether中的QuestContext.Frame转换为module.kether中的ScriptFrame
> 动作实现应该充分利用ScriptFrame提供的扩展功能，如变量管理和帧栈操作
