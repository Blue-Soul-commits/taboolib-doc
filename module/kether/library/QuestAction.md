# QuestAction

## 基本信息
- 类名和包路径: taboolib.library.kether.QuestAction
- 基本用途: 表示 Kether 脚本中的可执行动作，是所有动作的基类
- 类型: 抽象类
- 所属模块: minecraft-kether

## 类结构
### 公开静态方法
> noop(): QuestAction<T> -> 创建一个不执行任何操作的空动作实例

### 类方法
> process(@NotNull QuestContext.Frame frame): CompletableFuture<T> -> 处理动作的核心方法，接收一个帧并返回一个表示操作结果的 CompletableFuture

## 实现细节
- QuestAction 是一个泛型类，泛型 T 代表动作执行后返回的结果类型
- process 方法不应该被直接调用，而应该通过 QuestContext.Frame#newFrame(ParsedAction) 间接调用
- 动作执行是基于 CompletableFuture 的异步模型，支持非阻塞式执行

## 使用场景
> 作为 Kether 脚本中所有动作的基类，需要被具体的动作类继承并实现
> 在 Kether 脚本解析和执行过程中，通过 ParsedAction 封装后被 QuestContext 执行

## 注意事项
> 实现类必须重写 process 方法以提供具体的动作执行逻辑
> 由于是基于异步执行的模型，实现类需要正确处理异步操作和未来结果
