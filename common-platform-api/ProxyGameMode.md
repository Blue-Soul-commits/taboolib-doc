# ProxyGameMode
## 基本信息 
- 类名和包路径: taboolib.common.platform.ProxyGameMode
- 基本用途: 跨平台的游戏模式枚举，用于统一不同平台的游戏模式表示
- 类型: Kotlin 枚举类
- 所属模块: common-platform-api

## 类结构 
### 公开静态字段 
> CREATIVE -> 创造模式
> SURVIVAL -> 生存模式
> ADVENTURE -> 冒险模式
> SPECTATOR -> 旁观模式

### 公开静态方法 
> fromString(value: String): ProxyGameMode -> 将字符串或数字转换为对应的游戏模式枚举值

### 类内可被访问字段 
> 无类内可被访问字段

### 类方法
> 无实例方法

## 实现细节
- 定义了四种标准的游戏模式：CREATIVE（创造）、SURVIVAL（生存）、ADVENTURE（冒险）和 SPECTATOR（旁观）
- 提供了 fromString 静态方法，可以将字符串或数字形式的游戏模式转换为枚举值
- 字符串转换支持大小写不敏感的模式名称（如 "creative"、"CREATIVE"）
- 数字转换支持标准的游戏模式 ID（0=生存，1=创造，2=冒险，3=旁观）
- 当提供的字符串无法识别为有效的游戏模式时，会抛出异常

## 使用场景 
> 在跨平台插件中表示和操作玩家的游戏模式
> 解析来自配置文件或命令参数的游戏模式字符串
> 作为 ProxyPlayer.gameMode 属性的类型
> 在命令系统中处理游戏模式相关的参数

## 注意事项 
> fromString 方法在无法识别游戏模式时会抛出异常，调用时应做好异常处理
> 不同平台的游戏模式可能有细微差别，但基本的四种模式在所有平台上都是一致的
> 使用数字表示游戏模式时，应注意数字与模式的对应关系（0=生存，1=创造，2=冒险，3=旁观）