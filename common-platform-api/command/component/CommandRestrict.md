# CommandRestrict

## 基本信息
- 类名和包路径: taboolib.common.platform.command.component.CommandRestrict
- 基本用途: 命令参数约束器，用于验证动态参数的有效性
- 类型: 类（继承自 CommandBinder）
- 所属模块: TabooLib 平台命令组件模块

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> function: (sender: T, context: CommandContext<T>, argument: String) -> Boolean -> 参数验证函数

### 类方法
> exec(context: CommandContext<*>, argument: String): Boolean? -> 执行参数验证

## 实现细节
- 继承自 CommandBinder，利用其类型转换功能
- 持有一个函数引用，该函数包含参数验证的逻辑
- exec 方法负责处理参数验证过程：
  1. 尝试将命令上下文中的发送者转换为目标类型
  2. 如果转换成功，调用验证函数并返回结果
  3. 如果转换失败，返回 null
- 使用 @Suppress("UNCHECKED_CAST") 注解抑制类型转换警告
- 与 CommandExecutor 不同，验证失败不会触发错误处理，而是返回 null 或 false

## 使用场景
> 验证动态参数的有效性，如数字范围、玩家名称等
> 限制特定类型发送者的参数输入
> 在 CommandComponentDynamic 中使用，提供参数约束

## 注意事项
> 验证函数接收三个参数：发送者、命令上下文和当前参数
> 命令上下文会被复制并更新发送者为转换后的类型
> 返回值为 Boolean?，null 表示发送者类型不匹配，true/false 表示验证结果
> 与 CommandSuggestion 互斥，在 CommandComponentDynamic 中设置一个会清除另一个