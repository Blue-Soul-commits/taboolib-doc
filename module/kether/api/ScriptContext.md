# ScriptContext

## 基本信息
- 类名和包路径: taboolib.module.kether.ScriptContext
- 基本用途: Kether脚本的执行上下文，负责管理脚本执行状态、变量和执行者
- 类型: 开放类(open class)
- 所属模块: kether

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> create(script: Script, context: ScriptContext.() -> Unit = {}): ScriptContext -> 创建脚本上下文实例并执行配置函数

### 类内可被访问字段
> id: String -> 上下文标识符，默认为"null"
> sender: ProxyCommandSender? -> 脚本执行者，可读写属性
> breakLoop: Boolean -> 是否跳出循环的标志，可读写属性

### 类方法
> set(key: String, value: Any?) -> 设置变量，重载操作符"[]"
> get<T>(key: String, def: T? = null): T? -> 获取变量，重载操作符"[]"
> createExecutor(): ScriptSchedulerExecutor -> 创建脚本调度执行器

## 实现细节
- ScriptContext继承自AbstractQuestContext<ScriptContext>，提供了Kether脚本执行的核心功能
- 使用TabooLib的代理系统处理跨平台兼容性，sender属性可以适配不同平台的命令发送者
- 提供了便捷的变量访问方式，通过操作符重载实现"context[key] = value"和"context[key]"语法
- sender属性使用"@Sender"作为内部变量键，存储原始发送者对象，并提供类型转换
- breakLoop属性用于控制循环执行，使用"@BreakLoop"作为内部变量键
- 创建自定义的执行器ScriptSchedulerExecutor，负责脚本的任务调度

## 使用场景
> 作为Kether脚本执行的环境，管理执行状态和变量
> 存储脚本执行者信息，用于权限检查和消息发送
> 控制脚本流程，如循环和分支
> 在不同组件间共享数据和状态

## 注意事项
> id字段默认为"null"，应当在创建上下文后设置为有意义的值
> sender属性存储的是原始对象，但通过getter返回ProxyCommandSender类型
> 变量操作使用rootFrame的变量表，确保在整个脚本执行过程中可访问
> create静态方法使用了函数类型参数和lambda表达式，提供了DSL风格的上下文配置
