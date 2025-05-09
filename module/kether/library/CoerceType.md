# CoerceType

## 基本信息
- 类名和包路径: taboolib.library.kether.CoerceType
- 基本用途: 实现 ArgType 接口，用于将输入值转换（强制）为指定类型
- 类型: 泛型类
- 所属模块: minecraft-kether

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> function: Function<Object, Optional<T>> -> 用于将输入值转换为目标类型的函数
> type: String -> 转换目标的类型名称，用于生成错误消息

### 类方法
> CoerceType(function: Function<Object, Optional<T>>, type: String): CoerceType<T> -> 构造方法，接收转换函数和类型名称
> read(reader: QuestReader): T -> 从 QuestReader 读取下一个标记并应用转换函数，若转换失败则抛出异常

## 实现细节
- CoerceType 是 ArgType 接口的通用实现，用于处理基本数据类型的转换
- 内部使用 Function<Object, Optional<T>> 进行实际的类型转换操作
- 在转换失败时，会抛出包含具体错误信息的 LocalizedException
- 构造函数的访问级别为包级私有（package-private），主要通过 ArgTypes 类进行实例化

## 使用场景
> 用于在 Kether 脚本中读取和转换各种基本数据类型（如整数、浮点数、布尔值等）
> 通过 ArgTypes 类中的静态常量进行使用，如 ArgTypes.INT, ArgTypes.LONG 等
> 在自定义类型解析器时可作为参考实现

## 注意事项
> 转换函数应返回 Optional<T>，以便处理转换失败的情况
> 类型名称（type）在错误消息中使用，应提供有意义的描述