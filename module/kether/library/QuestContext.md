# QuestContext

## 基本信息
- 类名和包路径: taboolib.library.kether.QuestContext
- 基本用途: 表示 Kether 脚本执行的上下文环境，包含脚本执行状态、变量管理和帧栈
- 类型: 接口
- 所属模块: minecraft-kether

## 类结构
### 公开静态字段
> BASE_BLOCK: String -> 表示默认主要代码块的名称常量，值为 "main"

### 接口方法
> getService(): QuestService<? extends QuestContext> -> 获取当前上下文关联的服务实例
> getQuest(): Quest -> 获取当前上下文关联的脚本实例
> setExitStatus(ExitStatus exitStatus): void -> 设置脚本执行的退出状态
> getExitStatus(): Optional<ExitStatus> -> 获取脚本执行的退出状态
> runActions(): CompletableFuture<Object> -> 执行脚本内的动作并返回一个代表执行结果的 Future
> getExecutor(): Executor -> 获取用于执行脚本任务的执行器
> terminate(): void -> 终止脚本执行
> rootFrame(): Frame -> 获取脚本执行的根帧

## 实现细节
- QuestContext 含有两个内部接口：Frame 和 VarTable，分别表示执行帧和变量表
- Frame 接口提供了脚本执行的核心功能，包括管理动作执行、创建子帧和管理变量
- VarTable 接口负责变量存储和访问，支持变量的作用域和连锁查找
- 脚本执行采用帧栈结构，每个帧可以有父帧和子帧，形成执行树
- 变量表也采用链式结构，允许在父帧中查找变量

## 使用场景
> 作为 Kether 脚本执行的核心运行时环境
> 在脚本执行中管理变量、状态和控制流
> 通过帧栈机制支持嵌套执行和异步操作

## 注意事项
> Frame 实现了 AutoCloseable 接口，需要在执行完成后正确关闭以释放资源
> 变量名以 "~" 开头的变量会被限制在当前 VarTable 中，不会向上查找
> QuestContext 通常由 AbstractQuestContext 抽象类实现，提供了基础功能实现
