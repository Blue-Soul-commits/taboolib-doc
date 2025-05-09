# CommandRegister

## 基本信息
- 文件名和包路径: taboolib.common.platform.command.CommandRegister
- 基本用途: 提供命令注册的便捷函数
- 类型: Kotlin 文件（包含顶层函数）
- 所属模块: TabooLib 平台命令模块

## 函数

### command
> 注册一个完整功能的命令

**参数:**
- name: String -> 命令名
- aliases: List<String> -> 命令别名列表
- description: String -> 命令描述
- usage: String -> 命令用法
- permission: String -> 命令权限
- permissionMessage: String -> 命令权限提示
- permissionDefault: PermissionDefault -> 命令权限默认值
- permissionChildren: Map<String, PermissionDefault> -> 命令权限子节点
- newParser: Boolean -> 是否使用新解析器
- commandBuilder: CommandBase.() -> Unit -> 命令构建器函数

**返回值:** Unit

### simpleCommand
> 注册一个简易命令（无需构建复杂的命令树）

**参数:**
- name: String -> 命令名
- aliases: List<String> -> 命令别名列表
- description: String -> 命令描述
- usage: String -> 命令用法
- permission: String -> 命令权限
- permissionMessage: String -> 命令权限提示
- permissionDefault: PermissionDefault -> 命令权限默认值
- permissionChildren: Map<String, PermissionDefault> -> 命令权限子节点
- completer: CommandCompleter? -> 自定义补全器（可选）
- executor: (sender: ProxyCommandSender, args: Array<String>) -> Unit -> 命令执行函数

**返回值:** Unit

## 实现细节
- 两个函数都是对 registerCommand 函数的封装，提供了更便捷的接口
- command 函数创建完整的命令树，支持复杂的子命令和参数
- simpleCommand 函数创建简单命令，直接执行指定的函数，适合简单的命令逻辑
- 两个函数都会创建 CommandStructure、CommandExecutor 和 CommandCompleter
- command 函数中，执行器和补全器都会创建新的 CommandBase 实例并应用 commandBuilder
- simpleCommand 函数中，执行器直接调用提供的 executor 函数，补全器默认返回空列表

## 使用场景
> 注册插件命令，提供命令功能
> 创建复杂的命令树结构，支持子命令和参数
> 快速注册简单命令，无需构建复杂的命令树

## 注意事项
> command 函数每次执行或补全都会创建新的 CommandBase 实例
> simpleCommand 函数不支持子命令和复杂参数，但更轻量
> 两个函数都会自动注册命令到平台，无需额外步骤
> 权限默认值为 OP，可以根据需要修改
