# TypeTitle
## 基本信息
- 类名和包路径: taboolib.module.lang.gameside.TypeTitle
- 基本用途: 实现Type接口，用于发送标题和副标题消息
- 类型: 类
- 所属模块: minecraft-i18n

## 类结构
### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> title: String? -> 标题文本，可为null
> subtitle: String? -> 副标题文本，可为null
> fadein: Int -> 标题淡入时间(tick)，默认为0
> stay: Int -> 标题停留时间(tick)，默认为20
> fadeout: Int -> 标题淡出时间(tick)，默认为0

### 类方法
> init(source: Map<String, Any>): Unit -> 从配置源初始化标题参数
> send(sender: ProxyCommandSender, vararg args: Any): Unit -> 向指定接收者发送标题消息
> toString(): String -> 重写的toString方法，返回类的字符串表示

## 实现细节
- TypeTitle实现了Type接口，专门用于发送标题和副标题消息
- init方法从配置中加载标题参数：
  - title: 标题文本
  - subtitle: 副标题文本
  - fadein: 淡入时间，默认为0tick
  - stay: 停留时间，默认为20tick(1秒)
  - fadeout: 淡出时间，默认为0tick
- send方法根据接收者类型决定行为：
  - 如果接收者是ProxyPlayer，处理标题和副标题文本(应用翻译和变量替换)，然后使用sendTitle方法发送
  - 如果接收者不是ProxyPlayer，发送toString()的结果作为消息
- 如果title或subtitle为null，会使用空字符串("")代替
- toString方法返回类的字符串表示，但类名显示为"NodeTitle"而非"TypeTitle"，可能是历史遗留问题

## 使用场景
> 在配置文件中定义标题和副标题消息
> 向玩家发送重要通知或成就提示
> 在游戏事件(如关卡开始、结束)中显示大型文本提示
> 作为Language系统中的特殊消息类型，提供视觉突出的消息展示方式
> 创建沉浸式的游戏体验，通过屏幕中央的文本提供重要信息

## 注意事项
> title和subtitle字段可以为null，但在发送时会被转换为空字符串
> 非玩家接收者(如控制台)会收到标题描述的文本消息而非实际标题
> 时间参数(fadein, stay, fadeout)使用游戏tick作为单位，20tick等于1秒
> 标题会覆盖玩家屏幕中央的区域，可能影响玩家视野，应谨慎使用
> toString方法返回的类名为"NodeTitle"而非"TypeTitle"，可能导致混淆
