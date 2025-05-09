# ArgTypes

## 基本信息
- 类名和包路径: taboolib.library.kether.ArgTypes
- 基本用途: 提供预定义的参数类型转换器，用于在 Kether 脚本解析中获取各种数据类型
- 类型: 工具类
- 所属模块: minecraft-kether

## 类结构
### 公开静态字段
> INT: ArgType<Integer> -> 整数类型转换器，将文本转换为整数
> LONG: ArgType<Long> -> 长整数类型转换器，将文本转换为长整数
> DOUBLE: ArgType<Double> -> 双精度浮点数类型转换器，将文本转换为双精度浮点数
> BOOLEAN: ArgType<Boolean> -> 布尔类型转换器，将文本转换为布尔值
> DURATION: ArgType<Duration> -> 时间段类型转换器，将文本转换为 Duration 对象
> ACTION: ArgType<ParsedAction<?>> -> 动作类型转换器，将文本解析为 Kether 脚本动作

### 公开静态方法
> listOf<T>(argType: ArgType<T>): ArgType<List<T>> -> 创建一个列表类型转换器，用于解析指定元素类型的列表

### 类内可被访问字段
> 无

### 类方法
> 无

## 实现细节
- ArgTypes 类是一个工具类，包含多个预定义的 ArgType 转换器常量
- 基本类型（如 INT、LONG、DOUBLE、BOOLEAN）使用 CoerceType 实现，利用 taboolib.common5.Coerce 工具类进行类型转换
- DURATION 使用专门的 DurationType 实现，用于解析时间段表达式
- ACTION 使用方法引用 QuestReader::nextAction 实现，用于解析 Kether 脚本动作
- listOf 方法返回一个 ListType 实例，用于解析由方括号（[]）包围的列表结构

## 使用场景
> 在 Kether 脚本解析器中获取特定类型的参数
> 在实现自定义 Kether 动作时，用于解析动作所需的各种参数
> 通过 QuestReader 的 next 方法使用，如 reader.next(ArgTypes.INT)
> 使用 listOf 方法解析包含特定类型元素的列表，如 ArgTypes.listOf(ArgTypes.ACTION)

## 注意事项
> 使用 ArgTypes 时，应当了解基础的 Kether 脚本语法结构
> 如果解析失败，将抛出 LocalizedException 异常，需要适当处理
> 列表类型（通过 listOf 方法）需要在脚本中使用方括号语法，如 [1, 2, 3]
