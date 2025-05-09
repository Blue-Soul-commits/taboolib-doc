# CommandComponent

## 基本信息
- 类名和包路径: taboolib.common.platform.command.component.CommandComponent
- 基本用途: 命令组件抽象基类，用于构建命令树结构
- 类型: 抽象类
- 所属模块: TabooLib 平台命令组件模块

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> index: Int -> 命令组件在命令树中的索引位置
> optional: Boolean -> 是否为可选组件
> permission: String -> 使用该组件所需的权限
> commandExecutor: CommandExecutor<*>? -> 命令执行器
> children: ArrayList<CommandComponent> -> 子组件列表
> parent: CommandComponent? -> 父组件引用

### 类方法
> literal(vararg aliases: String, optional: Boolean, permission: String, hidden: Boolean, literal: CommandComponentLiteral.() -> Unit): CommandComponentLiteral -> 添加明文节点
> dynamic(comment: String, optional: Boolean, permission: String, dynamic: CommandComponentDynamic.() -> Unit): CommandComponentDynamic -> 添加动态节点
> exec<T>(function: ExecuteContext<T>.() -> Unit): Unit -> 创建简化执行器
> execute<T>(bind: Class<T>, function: (sender: T, context: CommandContext<T>, argument: String) -> Unit): Unit -> 创建执行器
> execute<T>(function: (sender: T, context: CommandContext<T>, argument: String) -> Unit): Unit -> 创建执行器（使用泛型推断）
> findChildren(context: CommandContext<*>): List<CommandComponent> -> 获取所有合法的子节点
> findChildren(context: CommandContext<*>, parameter: String): CommandComponent? -> 根据参数获取匹配的子节点

## 实现细节
- 作为命令组件的基类，提供了命令树构建的基础结构
- 支持两种类型的子节点：明文节点（固定文本）和动态节点（变量参数）
- 使用 DSL 风格的 API 设计，支持链式调用和 lambda 表达式
- 命令执行器使用泛型设计，支持不同类型的命令发送者
- 当节点设置了执行器后，其所有子节点自动变为可选节点
- 提供了权限检查机制，可以为每个节点设置独立的权限

## 使用场景
> 构建复杂的命令树结构
> 实现命令参数的自动补全和验证
> 支持多级子命令和参数的处理

## 注意事项
> 索引（index）表示命令参数在原始参数数组中的位置
> 可选（optional）节点表示命令执行时可以跳过该节点
> 权限（permission）为空字符串时表示不需要特定权限
> 当节点有执行器时，其所有子节点都会被标记为可选节点