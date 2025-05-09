# CommandUnknownNotify

## 基本信息
- 类名和包路径: taboolib.common.platform.command.component.CommandUnknownNotify
- 基本用途: 命令错误通知处理器，用于处理未知命令或参数错误的情况
- 类型: 类（继承自 CommandBinder）
- 所属模块: TabooLib 平台命令组件模块

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> function: (sender: T, context: CommandContext<T>, index: Int, state: Int) -> Unit -> 错误处理函数

### 类方法
> exec(context: CommandContext<*>, index: Int, state: Int): Unit -> 执行错误处理

## 实现细节
- 继承自 CommandBinder，利用其类型转换功能
- 持有一个函数引用，该函数包含错误通知的处理逻辑
- exec 方法负责处理错误通知过程：
  1. 尝试将命令上下文中的发送者转换为目标类型
  2. 如果转换成功，调用错误处理函数
  3. 如果转换失败，不执行任何操作
- 使用 @Suppress("UNCHECKED_CAST") 注解抑制类型转换警告
- 与其他命令组件不同，错误处理不会返回任何值

## 使用场景
> 处理未知命令的情况，如命令不存在或格式错误
> 处理参数错误的情况，如参数类型不匹配或超出范围
> 处理发送者类型不匹配的情况，如玩家专用命令被控制台执行

## 注意事项
> 错误处理函数接收四个参数：发送者、命令上下文、索引和状态
> 索引(index)表示错误发生的参数位置
> 状态(state)表示错误类型，通常有以下几种：
  - 0: 发送者类型不匹配
  - 1: 未知或不完整的命令
  - 2: 命令参数错误
> 命令上下文会被复制并更新发送者为转换后的类型
> 在 CommandBase 中通常有两个预定义的错误处理器：commandIncorrectSender 和 commandIncorrectCommand
