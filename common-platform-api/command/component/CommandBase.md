# CommandBase

## 基本信息
- 类名和包路径: taboolib.common.platform.command.component.CommandBase
- 基本用途: 命令树的根节点，处理命令执行和参数补全的核心类
- 类型: 类（继承自 CommandComponent）
- 所属模块: TabooLib 平台命令组件模块

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> result: Boolean -> 命令执行结果
> commandIncorrectSender: CommandUnknownNotify<*> -> 处理不匹配的命令发送者类型
> commandIncorrectCommand: CommandUnknownNotify<*> -> 处理不正确的命令格式

### 类方法
> execute(context: CommandContext<*>): Boolean -> 执行命令
> suggest(context: CommandContext<*>): List<String>? -> 提供命令参数补全建议
> incorrectSender(function: (sender: ProxyCommandSender, context: CommandContext<ProxyCommandSender>) -> Unit): Unit -> 自定义不匹配发送者处理
> incorrectCommand(function: (sender: ProxyCommandSender, context: CommandContext<ProxyCommandSender>, index: Int, state: Int) -> Unit): Unit -> 自定义不正确命令处理
> setResult(value: Boolean): Unit -> 设置命令执行结果

## 实现细节
- 作为命令组件树的根节点，索引值为 -1
- 提供命令执行和参数补全的核心逻辑
- 使用递归方式处理多级命令和参数
- 支持自定义错误处理和消息提示
- 命令执行过程中会更新上下文的索引和当前组件
- 提供默认的错误消息，支持多语言（通过 t() 函数）
- 使用 PlatformCommand 服务处理未知命令

## 使用场景
> 作为命令系统的入口点
> 处理命令执行和参数补全请求
> 提供错误处理和用户反馈

## 注意事项
> 命令执行和参数补全使用不同的逻辑路径
> 空参数（用户只输入命令名）是一种特殊情况，需要单独处理
> 命令执行结果通过 result 字段控制，可以通过 setResult 方法修改
> 错误处理支持两种状态：1 表示未知或不完整命令，2 表示参数错误