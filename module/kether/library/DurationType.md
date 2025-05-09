# DurationType

## 基本信息
- 类名和包路径: taboolib.library.kether.DurationType
- 基本用途: 实现 ArgType 接口，用于在 Kether 脚本中解析和转换持续时间字符串为 Java 的 Duration 对象
- 类型: 类
- 所属模块: minecraft-kether

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> 无

### 类方法
> read(reader: QuestReader): Duration -> 从 QuestReader 中读取下一个标记（token），将其转换为 Duration 对象

## 实现细节
- DurationType 实现了 ArgType<Duration> 接口，专门用于解析时间段表达式
- 在 read 方法中，它会从 QuestReader 获取下一个标记，并尝试将其转换为 ISO-8601 格式的持续时间表示
- 由于用户可能会使用简写格式，该类实现了一套预处理逻辑，将简写格式转换为标准的 ISO-8601 格式
- 预处理规则包括：
  1. 确保字符串包含 "T" 分隔符（时间部分标识）
  2. 如果包含 "D"（天）和 "H/M/S"（时/分/秒），则将 "D" 替换为 "DT"，以符合标准格式
  3. 确保字符串以 "P" 开头（Period 标识）
- 如果解析失败，抛出 LoadError.NOT_DURATION 错误

## 使用场景
> 在 Kether 脚本中解析表示时间段的参数，例如延迟、冷却时间等
> 通过 ArgTypes.DURATION 常量在脚本解析器中使用
> 在配置文件中使用标准的 ISO-8601 持续时间格式或简化格式

## 注意事项
> Duration 支持的格式必须符合 ISO-8601 标准或可转换为该标准
> Duration 对象表示的是一段时间间隔，不是一个特定的时间点
> 输入格式错误会导致 LocalizedException 异常
