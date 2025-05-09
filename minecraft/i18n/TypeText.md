# TypeText
## 基本信息
- 类名和包路径: taboolib.module.lang.TypeText
- 基本用途: 实现Type接口，用于处理普通文本消息，支持变量替换和国际化
- 类型: 类
- 所属模块: minecraft-i18n

## 类结构
### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> text: String? -> 存储消息文本内容，可为null

### 类方法
> constructor() -> 默认构造函数
> constructor(text: String) -> 带参数的构造函数，初始化text字段
> asText(sender: ProxyCommandSender, vararg args: Any): String? -> 获取处理后的文本内容，应用翻译和变量替换
> init(source: Map<String, Any>): Unit -> 从配置源初始化消息内容
> send(sender: ProxyCommandSender, vararg args: Any): Unit -> 向指定接收者发送消息
> toString(): String -> 重写的toString方法，返回类的字符串表示

## 实现细节
- TypeText实现了Type接口，是最基础的文本消息类型
- 支持两种构造方式：无参构造和带文本参数的构造
- 带参构造会检查文本是否为空，只有非空文本才会被设置
- asText方法对文本应用两重处理：翻译和变量替换
- init方法从配置中加载text字段，并处理空文本的情况
- send方法首先检查text是否为null，然后对文本进行处理并发送
- send方法根据Language.enableSimpleComponent的值决定发送方式：
  - 如果启用，将文本转换为组件(component())并发送
  - 如果禁用，直接发送普通文本消息
- toString方法返回类的字符串表示，但类名显示为"NodeText"而非"TypeText"，可能是历史遗留问题

## 使用场景
> 在配置文件中定义基础文本消息
> 实现多语言支持的文本消息系统
> 在游戏内发送带有变量替换的消息
> 作为Language系统中的基础文本消息类型
> 在不需要复杂格式的场景中使用，提供简单的文本处理功能

## 注意事项
> text字段可能为null，使用前需要进行空检查
> 配置中的text字段如果为空，会被设置为null
> 发送方式受Language.enableSimpleComponent全局设置影响
> 变量替换使用replaceWithOrder方法，支持%s格式和命名变量
> toString方法返回的类名为"NodeText"而非"TypeText"，可能导致混淆
> 与TypeSimpleText相比，TypeText更简单，不支持特殊格式语法

