# SuggestContext

## 基本信息
- 类名和包路径: taboolib.common.platform.command.component.SuggestContext
- 基本用途: 命令补全上下文，简化命令补全时的参数传递
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

### 类方法
> 作为数据类，自动生成了 equals()、hashCode()、toString() 和 copy() 方法

## 实现细节
- 使用 Kotlin 的数据类特性，自动实现了常用方法
- 泛型设计，支持不同类型的命令发送者
- 封装了命令补全所需的两个核心元素：发送者和上下文
- 主要用于 CommandSuggestion 的函数中，简化命令补全函数的参数传递

## 使用场景
> 在命令补全函数中使用，提供更简洁的访问方式
> 作为 CommandSuggestion 的补全函数参数，简化补全处理
> 在 ExtraComponentSuggest 的扩展函数中使用

## 注意事项
> 与 ExecuteContext 类似，但不包含 args 参数
> 通过 ctx 可以访问完整的命令上下文，包括所有参数和选项
> 泛型参数 T 通常是命令发送者的类型，如 Player、ConsoleCommandSender 等
> 在命令补全过程中使用，而非命令执行过程
