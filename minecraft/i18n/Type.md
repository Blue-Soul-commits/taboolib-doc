# Type
## 基本信息
- 类名和包路径: taboolib.module.lang.Type
- 基本用途: 定义TabooLib国际化系统中消息类型的接口，用于处理不同形式的消息发送
- 类型: 接口
- 所属模块: minecraft-i18n

## 类结构
### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> 无字段（接口本身没有字段）

### 类方法
> init(source: Map<String, Any>): Unit -> 初始化消息类型，从配置源中加载数据
> send(sender: ProxyCommandSender, vararg args: Any): Unit -> 向指定接收者发送消息，支持可变参数
> String.translate(sender: ProxyCommandSender, vararg args: Any): String -> 扩展函数，应用所有文本转换器处理字符串

## 实现细节
- Type接口是TabooLib国际化系统的核心组件，定义了不同消息类型的基本行为
- 接口设计支持多种消息形式，如普通文本、标题、声音、JSON格式等
- init方法用于从配置中初始化消息类型，配置通常是YAML格式的键值对
- send方法用于向指定接收者发送消息，支持传递额外参数用于替换占位符
- translate扩展函数应用Language.textTransfer中的所有文本转换器处理字符串
- 文本转换器可以处理颜色代码、变量替换、国际化等功能

## 使用场景
> 实现不同类型的消息发送，如文本消息、标题、声音等
> 在配置文件中定义复杂的消息结构，通过Type接口统一处理
> 支持国际化消息系统，根据接收者的语言偏好发送适当的消息
> 与TabooLib的事件系统配合，响应玩家操作发送相应消息
> 在插件开发中提供统一的消息发送接口，简化消息处理逻辑

## 注意事项
> 实现此接口的类需要提供init和send方法的具体实现
> 配置格式需要遵循特定的结构，如示例中的type、text等字段
> translate方法依赖于Language.textTransfer，确保已正确配置文本转换器
> 不同的消息类型可能需要不同的配置参数，如title需要fadein、stay、fadeout等
> 在处理JSON格式消息时，需要注意args参数与text的对应关系

