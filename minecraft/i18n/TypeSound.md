# TypeSound
## 基本信息
- 类名和包路径: taboolib.module.lang.gameside.TypeSound
- 基本用途: 实现Type接口，用于播放声音效果
- 类型: 类
- 所属模块: minecraft-i18n

## 类结构
### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> sound: String -> 声音的标识符，使用lateinit延迟初始化
> volume: Float -> 声音的音量，默认为1.0f
> pitch: Float -> 声音的音调，默认为1.0f
> resource: Boolean -> 是否为资源包声音，默认为false

### 类方法
> init(source: Map<String, Any>): Unit -> 从配置源初始化声音参数
> send(sender: ProxyCommandSender, vararg args: Any): Unit -> 向指定接收者播放声音
> toString(): String -> 重写的toString方法，返回类的字符串表示

## 实现细节
- TypeSound实现了Type接口，专门用于播放声音效果
- init方法从配置中加载声音参数：
  - sound: 必需参数，声音的标识符
  - volume/v: 可选参数，声音的音量，默认为1.0f
  - pitch/p: 可选参数，声音的音调，默认为1.0f
  - resource: 可选参数，是否为资源包声音，接受"1"、"true"或"yes"作为肯定值
- send方法根据接收者类型决定行为：
  - 如果接收者是ProxyPlayer，根据resource字段决定播放方式：
    - 如果resource为true，使用playSoundResource方法播放资源包声音
    - 如果resource为false，使用playSound方法播放标准声音，并捕获可能的IllegalArgumentException
  - 如果接收者不是ProxyPlayer，发送toString()的结果作为消息
- toString方法返回类的字符串表示，但类名显示为"NodeSound"而非"TypeSound"，可能是历史遗留问题

## 使用场景
> 在配置文件中定义声音效果
> 向玩家播放游戏内置声音或资源包声音
> 作为Language系统中的特殊消息类型，提供听觉反馈
> 在游戏事件、成就或通知中增加声音效果
> 创建沉浸式的游戏体验，通过声音提供额外的反馈

## 注意事项
> sound字段使用lateinit修饰，如果在init之前访问会抛出UninitializedPropertyAccessException
> 配置中必须包含"sound"键，否则可能导致异常
> 非玩家接收者(如控制台)会收到声音描述的文本消息而非实际声音
> 播放标准声音时会捕获IllegalArgumentException，这通常是由无效的声音标识符引起的
> toString方法返回的类名为"NodeSound"而非"TypeSound"，可能导致混淆
