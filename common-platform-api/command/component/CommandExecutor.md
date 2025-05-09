# CommandExecutor

## 基本信息
- 类名和包路径: taboolib.common.platform.command.component.CommandExecutor
- 基本用途: 命令执行器，处理命令的实际执行逻辑
- 类型: 类（继承自 CommandBinder）
- 所属模块: TabooLib 平台命令组件模块

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> function: (sender: T, context: CommandContext<T>, argument: String) -> Unit -> 命令执行函数

### 类方法
> exec(commandBase: CommandBase, context: CommandContext<*>, argument: String): Unit -> 执行命令逻辑

## 实现细节
- 继承自 CommandBinder，利用其类型转换功能
- 持有一个函数引用，该函数包含命令的实际执行逻辑
- exec 方法负责处理命令执行过程：
  1. 尝试将命令上下文中的发送者转换为目标类型
  2. 如果转换成功，调用执行函数
  3. 如果转换失败，触发不匹配发送者类型的错误处理
- 使用 @Suppress("UNCHECKED_CAST") 注解抑制类型转换警告

## 使用场景
> 定义命令节点的执行逻辑
> 处理特定类型发送者的命令执行
> 作为命令组件树中叶子节点的执行器

## 注意事项
> 执行函数接收三个参数：发送者、命令上下文和当前参数
> 命令上下文会被复制并更新发送者为转换后的类型
> 如果发送者类型不匹配，将触发 commandIncorrectSender 错误处理
