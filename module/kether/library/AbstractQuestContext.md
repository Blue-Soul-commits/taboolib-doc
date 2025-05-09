# AbstractQuestContext

## 基本信息
- 类名和包路径: taboolib.library.kether.AbstractQuestContext
- 基本用途: 提供 QuestContext 接口的通用实现，管理 Kether 脚本的执行上下文
- 类型: 抽象类
- 所属模块: minecraft-kether

## 类结构
### 受保护字段
> service: QuestService<T> -> 关联的脚本服务实例
> rootFrame: Frame -> 根执行帧
> quest: Quest -> 当前执行的脚本
> executor: QuestExecutor -> 任务执行器
> exitStatus: ExitStatus -> 脚本退出状态
> future: CompletableFuture<Object> -> 脚本执行的 Future 对象

### 构造方法
> AbstractQuestContext(QuestService<T> service, Quest quest, String playerIdentifier): constructor -> 创建上下文实例

### 受保护方法
> createExecutor(): Executor -> 创建任务执行器，由子类实现
> createRootFrame(): Frame -> 创建根执行帧

### 公开方法
> getService(): QuestService<T> -> 获取脚本服务实例
> getQuest(): Quest -> 获取当前执行的脚本
> setExitStatus(ExitStatus exitStatus): void -> 设置脚本退出状态
> getExitStatus(): Optional<ExitStatus> -> 获取脚本退出状态
> getExecutor(): QuestExecutor -> 获取任务执行器
> rootFrame(): Frame -> 获取根执行帧
> runActions(): CompletableFuture<Object> -> 运行脚本中的动作
> terminate(): void -> 终止脚本执行

## 内部类
### QuestExecutor
任务执行器，实现 Executor 接口，用于执行脚本中的任务。

### AbstractFrame
抽象帧类，提供 QuestContext.Frame 接口的基础实现。

### SimpleNamedFrame
命名帧实现，用于执行脚本中的代码块。

### SimpleActionFrame
动作帧实现，用于执行单个脚本动作。

### SimpleVarTable
变量表实现，管理脚本中的变量。

## 实现细节
- 使用递归的帧结构来执行脚本，每个帧可以包含子帧
- 帧执行采用异步模式，返回 CompletableFuture 对象
- 变量表采用链式结构，支持作用域和变量查找
- 脚本执行状态由 ExitStatus 管理，可以表示运行、等待或完成状态
- 终止脚本时会关闭所有帧并完成相关的 Future 对象

## 使用场景
> 作为 Kether 脚本执行引擎的核心组件
> 管理脚本执行状态、变量和帧栈
> 提供异步执行和变量访问机制

## 注意事项
> 子类需要实现 createExecutor 方法提供适当的执行器
> 变量名以 "~" 前缀的变量会被限制在当前作用域
> 终止脚本会触发异常完成，释放所有资源
