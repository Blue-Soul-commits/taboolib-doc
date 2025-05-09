# TypeCommand
## 基本信息
- 类名和包路径: taboolib.module.lang.gameside.TypeCommand
- 基本用途: 实现Type接口，用于执行命令操作
- 类型: 类
- 所属模块: minecraft-i18n

## 类结构
### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> command: List<String>? -> 存储要执行的命令列表，可为null

### 类方法
> init(source: Map<String, Any>): Unit -> 从配置源初始化命令列表
> send(sender: ProxyCommandSender, vararg args: Any): Unit -> 执行命令列表中的所有命令
> toString(): String -> 重写的toString方法，返回类的字符串表示

## 实现细节
- TypeCommand实现了Type接口，专门用于执行命令操作
- init方法从配置中获取"command"键对应的值，并转换为字符串列表
- send方法遍历命令列表，对每个命令执行以下处理：
  - 将"@p"替换为发送者的名称
  - 应用文本翻译(translate)
  - 应用变量替换(replaceWithOrder)
  - 通过控制台(console)执行处理后的命令
- 所有命令都是以控制台身份执行的，具有最高权限
- toString方法返回类的字符串表示，包含command字段的值

## 使用场景
> 在配置文件中定义需要执行的命令序列
> 通过Language系统触发服务器命令执行
> 实现基于消息的命令自动化
> 在特定事件或条件下执行一系列预定义的命令
> 创建可配置的命令宏，通过单一触发执行多个命令

## 注意事项
> command字段可能为null，使用前需要进行空检查
> 所有命令都是以控制台身份执行的，具有最高权限，使用时需谨慎
> "@p"是一个特殊标记，会被替换为发送者的名称，类似于Minecraft的目标选择器
> 命令执行不会返回任何结果或状态信息
> 由于命令是通过控制台执行的，不会有权限检查，可能导致安全风险

