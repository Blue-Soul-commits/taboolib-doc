# ExecuteContext

## 基本信息
- 类名和包路径: taboolib.common.platform.command.component.ExecuteContext
- 基本用途: 命令执行上下文，简化命令执行时的参数传递
- 类型: 数据类 (data class)
- 所属模块: TabooLib 平台命令组件模块

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> sender: T -> 命令发送者
> ctx: CommandContext<T> -> 命令上下文
> args: String -> 当前参数字符串

### 类方法
> 作为数据类，自动生成了 equals()、hashCode()、toString() 和 copy() 方法

## 实现细节
- 使用 Kotlin 的数据类特性，自动实现了常用方法
- 泛型设计，支持不同类型的命令发送者
- 封装了命令执行所需的三个核心元素：发送者、上下文和参数
- 主要用于 CommandComponent 的 exec 方法中，简化命令执行函数的参数传递

## 使用场景
> 在命令执行函数中使用，提供更简洁的访问方式
> 作为 CommandExecutor 的执行函数参数，简化命令处理
> 在 CommandComponent 的 exec 扩展方法中使用

## 注意事项
> 与 SuggestContext 类似，但包含了额外的 args 参数
> args 参数通常是当前命令节点对应的输入参数
> 通过 ctx 可以访问完整的命令上下文，包括所有参数和选项
> 泛型参数 T 通常是命令发送者的类型，如 Player、ConsoleCommandSender 等