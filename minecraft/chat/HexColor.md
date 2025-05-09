# HexColor
## 基本信息
- 类名和包路径: taboolib.module.chat.HexColor
- 基本用途: 提供多种格式的颜色代码转换功能，支持RGB、HEX以及中英文颜色名称
- 类型: 工具类
- 所属模块: minecraft-chat

## 类结构
### 公开静态字段
> isLegacy: boolean -> 标识当前环境是否为旧版本（不支持RGB颜色）

### 公开静态方法
> translate(in: String): String -> 将字符串中的特殊颜色表达式转换为Minecraft支持的颜色代码
> getColorCode(color: int): String -> 根据整数颜色值获取对应的颜色代码字符串

### 类内可被访问字段
> 无公开字段

### 类方法
> arrayAppend(chars: char[], in: char): char[] -> 向字符数组末尾添加一个字符
> toString(chars: char[]): String -> 将字符数组转换为字符串
> toInt(chars: char[], start: int, end: int): int -> 将字符数组的指定范围转换为整数

## 实现细节
- 通过静态初始化块检测当前环境是否支持RGB颜色，如果不支持则将isLegacy设置为true
- translate方法支持多种颜色格式的转换：
  - &{255-255-255} 或 &{255,255,255} 格式的RGB代码
  - &{#FFFFFF} 格式的HEX代码
  - &{BLUE} 格式的英文颜色名称
  - &{蓝} 格式的中文颜色名称
- 在1.20.4版本中，由于不再支持&r/§r重置颜色的写法，方法会将其替换为&f/§f（白色）
- 如需恢复默认颜色，建议使用SimpleComponent中的reset属性

## 使用场景
> 在聊天消息、物品名称、Lore等需要使用颜色的地方，可以使用更灵活的颜色表达式
> 在国际化插件中，可以同时支持中英文颜色名称，提高用户体验
> 在需要使用RGB颜色的现代Minecraft版本中，提供了简便的颜色表达方式

## 注意事项
> 在旧版本Minecraft中（不支持RGB颜色的版本），会自动降级使用传统的颜色代码
> 1.20.4版本不再支持&r/§r重置颜色的写法，会被自动替换为白色(&f/§f)
> 使用中文颜色名称时，需要确保StandardColors枚举中包含对应的颜色名称

