# CommandContext

## 基本信息
- 类名和包路径: taboolib.common.platform.command.CommandContext
- 基本用途: 命令上下文，封装命令执行时的环境和参数处理
- 类型: 数据类
- 所属模块: TabooLib 平台命令模块

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> sender: T -> 命令发送者（泛型类型）
> command: CommandStructure -> 命令结构
> name: String -> 命令名称
> commandCompound: CommandBase -> 命令组件
> newParser: Boolean -> 是否使用新解析器
> rawArgs: Array<String> -> 原始参数数组
> index: Int -> 当前参数索引
> currentComponent: CommandComponent? -> 当前命令组件
> lineParser: CommandLineParser? -> 命令行解析器实例
> realArgs: Array<String> -> 实际参数数组

### 类方法
> sender(): ProxyCommandSender -> 获取命令发送者
> player(): ProxyPlayer -> 获取命令发送者（作为玩家）
> checkPermission(permission: String): Boolean -> 检查发送者是否有指定权限
> hasOption(id: String): Boolean -> 检查是否有指定选项
> option(vararg id: String): String? -> 获取指定选项的值
> options(): Map<String, String> -> 获取所有选项
> args(): Array<String> -> 获取所有参数
> self(): String -> 获取当前位置参数
> get(id: String): String -> 根据节点名称获取参数
> getOrNull(id: String): String? -> 根据节点名称获取参数（可空）
> get(index: Int): String -> 根据索引获取参数（已弃用）
> getOrNull(index: Int): String? -> 根据索引获取参数（可空，已弃用）
> argument(offset: Int): String -> 获取相对于当前索引的参数（已弃用）
> argumentOrNull(offset: Int): String? -> 获取相对于当前索引的参数（可空，已弃用）

## 实现细节
- 使用泛型设计，支持不同类型的命令发送者
- 支持新旧两种命令解析器，通过 newParser 字段区分
- 新解析器使用 CommandLineParser 解析命令行，支持选项和引号等高级特性
- 提供了多种方式获取参数，包括按节点名称和索引
- 实现了 equals 和 hashCode 方法，支持数据类的比较和哈希操作
- 内部使用递归方法 process 查找命令组件对应的参数索引

## 使用场景
> 在命令执行过程中传递和处理命令上下文
> 提供对命令参数和选项的访问
> 支持基于节点名称的参数获取，提高代码可读性

## 注意事项
> 使用新解析器时，必须通过 hasOption、option 等方法获取选项
> 旧的基于索引的参数获取方法已被弃用，应使用基于节点名称的方法
> 调用 player() 方法前应确保发送者是玩家，否则会抛出 ClassCastException
> 使用新解析器相关方法时，如果命令未启用新解析器，会抛出异常