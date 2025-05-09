# SimpleCommand
## 基本信息 
- 类名和包路径: taboolib.common.platform.command.SimpleCommand
- 基本用途: 提供基于注解的命令注册系统，简化命令的创建和管理
- 类型: Kotlin 文件，包含注解、函数和类
- 所属模块: common-platform-api

## 类结构 
### 公开静态字段 
> 无公开静态字段

### 公开静态方法 
> mainCommand(func: CommandBase.() -> Unit): SimpleCommandMain -> 创建主命令处理函数
> subCommand(func: CommandComponent.() -> Unit): SimpleCommandBody -> 创建子命令处理函数
> subCommandExec<T>(func: ExecuteContext<T>.() -> Unit): SimpleCommandBody -> 创建带执行上下文的子命令处理函数

### 类内可被访问字段 
> 无类内可被访问字段（文件级别）

### 类方法
> 无类方法（文件级别）

## 实现细节
- 使用注解 `@CommandHeader` 标记命令类，定义命令的基本属性
- 使用注解 `@CommandBody` 标记命令字段，定义子命令的属性
- `SimpleCommandRegister` 类负责扫描和注册带有这些注解的类和字段
- 通过反射机制自动构建命令树结构，支持多层嵌套的子命令
- 支持新的命令解析器（newParser），可以处理带选项的命令
- 命令注册在 `LifeCycle.ENABLE` 阶段进行，确保在插件启用时注册

## 使用场景 
> 创建具有多层子命令的复杂命令系统
> 使用注解方式定义命令，避免冗长的命令注册代码
> 实现权限分层的命令系统，不同子命令可以有不同的权限要求

## 注意事项 
> 命令类必须使用 `@CommandHeader` 注解，否则不会被注册
> 子命令字段必须使用 `@CommandBody` 注解，并且类型为 `SimpleCommandBody` 或其他自定义类型
> 使用 `mainCommand` 函数创建的主命令会在根命令执行时调用
> 子命令可以设置为可选（optional=true），允许在没有子命令时执行父命令
> 隐藏子命令（hidden=true）不会在命令帮助中显示，但仍然可以执行
