# TypeList
## 基本信息
- 类名和包路径: taboolib.module.lang.TypeList
- 基本用途: 实现Type接口，用于管理和发送多个Type实例的集合
- 类型: 类
- 所属模块: minecraft-i18n

## 类结构
### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> list: List<Type> -> 存储Type实例的列表，通过构造函数传入

### 类方法
> asTextList(sender: ProxyCommandSender, vararg args: Any): List<String> -> 提取所有TypeText类型的实例并获取其文本内容
> init(source: Map<String, Any>): Unit -> 初始化方法（空实现）
> send(sender: ProxyCommandSender, vararg args: Any): Unit -> 向指定接收者发送所有Type实例的消息
> toString(): String -> 重写的toString方法，返回TypeList的字符串表示

## 实现细节
- TypeList实现了Type接口，作为多个Type实例的容器
- 构造函数接收一个Type列表，用于初始化内部的list字段
- asTextList方法使用filterIsInstance筛选出TypeText类型的实例，并调用它们的asText方法获取文本内容
- init方法是空实现，因为TypeList的初始化通过构造函数完成，不需要从配置中加载
- send方法遍历list中的所有Type实例，依次调用它们的send方法
- toString方法返回TypeList的字符串表示，包含list的内容

## 使用场景
> 在需要发送多种类型消息的场景中使用，如同时发送文本和标题
> 作为Language系统中的消息组合器，将多个消息类型组合为一个单元
> 在配置文件中定义由多个部分组成的复杂消息
> 批量处理和发送一组相关的消息
> 提取特定类型(TypeText)的消息内容，用于进一步处理

## 注意事项
> init方法是空实现，TypeList的初始化依赖于构造函数传入的list
> asTextList方法只会提取TypeText类型的实例，其他类型会被忽略
> send方法会按list中的顺序依次发送所有消息
> 在使用TypeList时，需要确保list中的Type实例已经正确初始化
> TypeList本身不处理消息内容，只是作为Type实例的容器和调度器
