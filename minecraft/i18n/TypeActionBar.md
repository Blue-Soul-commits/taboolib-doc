# TypeActionBar
## 基本信息
- 类名和包路径: taboolib.module.lang.gameside.TypeActionBar
- 基本用途: 实现Type接口，用于发送动作栏(ActionBar)消息
- 类型: 类
- 所属模块: minecraft-i18n

## 类结构
### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> text: String -> 存储动作栏消息文本内容，使用lateinit延迟初始化

### 类方法
> init(source: Map<String, Any>): Unit -> 从配置源初始化消息内容
> send(sender: ProxyCommandSender, vararg args: Any): Unit -> 向指定接收者发送动作栏消息
> toString(): String -> 重写的toString方法，返回类的字符串表示

## 实现细节
- TypeActionBar实现了Type接口，专门用于处理动作栏消息
- text字段使用lateinit延迟初始化，在init方法中赋值
- init方法从配置中获取"text"键对应的值，并转换为字符串
- send方法首先对文本应用两重处理：翻译和变量替换
- send方法根据接收者类型决定发送方式：
  - 如果接收者是ProxyPlayer，使用sendActionBar方法发送动作栏消息
  - 如果接收者不是ProxyPlayer，退化为普通消息发送(sendMessage)
- toString方法返回类的字符串表示，但类名显示为"NodeActionBar"而非"TypeActionBar"，可能是历史遗留问题

## 使用场景
> 在配置文件中定义动作栏消息
> 向玩家发送临时提示信息，显示在屏幕中央底部
> 显示状态更新、计时器或其他需要玩家注意但不干扰主聊天框的信息
> 作为Language系统中的特殊消息类型，提供更丰富的消息展示方式
> 在游戏内UI中提供非侵入式的反馈信息

## 注意事项
> text字段使用lateinit修饰，如果在init之前访问会抛出UninitializedPropertyAccessException
> 配置中必须包含"text"键，否则可能导致异常
> 非玩家接收者(如控制台)会收到普通消息而非动作栏消息
> 动作栏消息通常只会显示几秒钟，不适合长时间展示的重要信息
> toString方法返回的类名为"NodeActionBar"而非"TypeActionBar"，可能导致混淆

