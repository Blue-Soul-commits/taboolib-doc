# Source
## 基本信息
- 类名和包路径: taboolib.module.chat.Source
- 基本用途: 定义消息源的通用接口，提供多种格式转换和发送消息的方法
- 类型: 接口
- 所属模块: minecraft-chat

## 类结构
### 公开静态字段
> 无静态字段

### 公开静态方法
> 无静态方法

### 类内可被访问字段
> 无字段

### 类方法
> toRawMessage(): String -> 将消息转换为原始JSON格式的消息字符串
> toLegacyText(): String -> 将消息转换为带颜色代码的传统文本格式
> toPlainText(): String -> 将消息转换为不带任何格式的纯文本
> toSpigotObject(): BaseComponent -> 将消息转换为Spigot的BaseComponent对象
> toLegacyRawMessage(): RawMessage -> 将消息转换为TabooLib的RawMessage对象
> broadcast(): Unit -> 将消息广播给所有在线玩家
> sendTo(sender: ProxyCommandSender): Unit -> 将消息发送给指定的命令发送者

## 实现细节
- Source接口定义了消息源的基本行为，包括多种格式转换和发送方法
- 提供了从复杂消息对象到各种格式（原始JSON、传统文本、纯文本等）的转换能力
- 支持将消息直接广播给所有玩家或发送给特定的命令发送者
- 接口设计遵循了Kotlin的风格，使用简洁的函数名和返回类型

## 使用场景
> 作为TabooLib聊天模块中各种消息类型的统一接口
> 在需要处理不同格式消息的系统中，提供一致的转换和发送方法
> 在插件开发中，用于创建可以以多种方式呈现和发送的消息
> 与ComponentText等其他聊天组件接口配合，构建完整的消息处理系统

## 注意事项
> 实现此接口的类需要提供所有方法的具体实现
> toSpigotObject()方法返回Spigot的BaseComponent对象，在非Spigot环境中可能需要特殊处理
> 发送消息的方法(broadcast和sendTo)依赖于TabooLib的平台抽象层
> 不同的实现类可能对各种转换方法有不同的处理逻辑
