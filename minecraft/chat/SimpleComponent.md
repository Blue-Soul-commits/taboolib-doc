# SimpleComponent
## 基本信息
- 类名和包路径: taboolib.module.chat.SimpleComponent
- 基本用途: 提供简化的组件构建接口，用于创建和发送聊天消息
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
> build(): ComponentText -> 构建为ComponentText对象，不进行任何转换
> build(transfer: TextTransfer.() -> Unit): ComponentText -> 构建为ComponentText对象，并应用自定义转换
> buildColored(): ComponentText -> 构建为ComponentText对象，并应用颜色转换
> buildColored(transfer: TextTransfer.() -> Unit): ComponentText -> 构建为ComponentText对象，应用颜色转换和自定义转换
> buildToRaw(): String -> 直接构建为原始JSON格式的消息字符串
> buildToRaw(transfer: TextTransfer.() -> Unit): String -> 直接构建为原始JSON格式的消息字符串，并应用自定义转换
> broadcast(): Unit -> 构建消息并广播给所有玩家
> sendTo(sender: ProxyCommandSender): Unit -> 构建消息并发送给指定的命令发送者

## 实现细节
- SimpleComponent接口提供了一系列构建和发送消息的便捷方法
- 只有build(transfer: TextTransfer.() -> Unit)方法需要实现类提供具体实现，其他方法都有默认实现
- buildColored方法会自动应用colored()转换，使文本带有颜色
- buildToRaw方法会将构建的ComponentText直接转换为原始JSON格式
- broadcast和sendTo方法利用构建的ComponentText对象的相应方法发送消息
- 所有方法都支持使用TextTransfer函数类型的参数进行自定义转换

## 使用场景
> 在需要简化聊天消息构建过程的插件中使用
> 作为更复杂的聊天组件系统的基础接口
> 在需要支持文本转换和颜色处理的消息系统中使用
> 与ComponentText和Source接口配合，构建完整的消息处理流程

## 注意事项
> 实现此接口的类只需要提供build(transfer: TextTransfer.() -> Unit)方法的具体实现
> TextTransfer是一个函数类型，用于对文本进行自定义转换
> colored()是TextTransfer的一个扩展函数，用于应用颜色转换
> 发送消息的方法依赖于构建的ComponentText对象，而ComponentText需要实现Source接口的相关方法

