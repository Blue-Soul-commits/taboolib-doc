# Command
## 基本信息 
- 类名和包路径: taboolib.common.platform.function.Command
- 基本用途: 提供跨平台命令注册和注销的顶层函数集合
- 类型: Kotlin 文件，包含顶层函数
- 所属模块: common-platform-api

## 类结构 
### 公开静态字段 
> 无公开静态字段（文件级别）

### 公开静态方法 
> registerCommand(command: CommandStructure, executor: CommandExecutor, completer: CommandCompleter, commandBuilder: CommandBase.() -> Unit): Unit -> 注册一个命令
> unregisterCommand(command: CommandStructure): Unit -> 注销一个命令及其所有别名
> unregisterCommand(command: String): Unit -> 注销指定名称的命令
> unregisterCommands(): Unit -> 注销所有命令

### 类内可被访问字段 
> 无类内可被访问字段（文件级别）

### 类方法
> 无类方法（文件级别）

## 实现细节
- 所有函数都是顶层函数，可以直接导入使用，无需通过类实例调用
- 内部通过 PlatformFactory.getService<PlatformCommand>() 获取平台命令服务实例
- registerCommand 函数用于注册命令，接收命令结构、执行器、补全器和命令构建器
- 提供了两个版本的 unregisterCommand 函数，一个接收 CommandStructure 对象，另一个接收命令名称字符串
- unregisterCommands 函数用于一次性注销所有已注册的命令

## 使用场景 
> 手动注册和注销跨平台命令
> 在插件禁用时清理命令
> 动态创建和移除命令
> 作为 TabooLib 命令系统的底层支持函数

## 注意事项 
> 这些函数依赖于 PlatformCommand 服务，确保在适当的生命周期阶段调用
> 通常不需要直接调用 registerCommand，而是使用更高级的 command 函数
> unregisterCommand(CommandStructure) 会注销命令本身及其所有别名
> 在插件禁用时，TabooLib 会自动调用 unregisterCommands 清理命令