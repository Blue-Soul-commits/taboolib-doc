# RemoteActionParser

## 基本信息
- 类名和包路径: taboolib.module.kether.RemoteActionParser
- 基本用途: Kether脚本引擎的远程动作解析器，用于跨插件/容器解析脚本动作
- 类型: 类
- 所属模块: kether

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> remote: OpenContainer -> 远程容器实例，用于进行跨容器通信
> action: String -> 动作名称
> namespace: String -> 动作所属的命名空间，默认为"kether"

### 类方法
> resolve<T>(resolver: QuestReader): QuestAction<T> -> 实现QuestActionParser接口的方法，解析动作

## 实现细节
- RemoteActionParser实现了QuestActionParser接口，用于解析远程定义的脚本动作
- 构造函数接收远程容器、动作名称和命名空间参数
- resolve方法通过StandardChannel.REMOTE_RESOLVE通道发送解析请求到远程容器
- 使用当前插件ID(pluginId)作为来源标识
- 如果远程解析失败(result.isFailed)，会抛出错误
- 解析成功后返回RemoteQuestAction实例，包装远程动作的执行逻辑

## 使用场景
> 跨插件解析和执行Kether脚本动作
> 允许一个插件使用另一个插件注册的动作
> 在不同ClassLoader环境下共享脚本功能
> 实现模块化的Kether扩展系统

## 注意事项
> 依赖远程容器的可用性，如果远程容器不可用则解析失败
> 远程通信可能带来性能开销，特别是频繁解析时
> 错误处理相对简单，只提供基本的错误信息
> 与StandardChannel和RemoteQuestAction配合使用，构成完整的远程执行系统
