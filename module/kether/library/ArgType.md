# ArgType

## 基本信息
- 类名和包路径: taboolib.library.kether.ArgType
- 基本用途: 用于从 QuestReader 中读取并解析特定类型的参数
- 类型: 接口（泛型）
- 所属模块: minecraft-kether

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> 无

### 类方法
> read(reader: QuestReader): T -> 从 QuestReader 中读取并解析为指定类型的值，可能抛出 LocalizedException

## 实现细节
- ArgType 是一个泛型接口，用于解析特定类型的参数
- 该接口只有一个方法 read，接收 QuestReader 作为参数，返回泛型类型 T
- 在解析过程中可能会抛出 LocalizedException 异常
- 实现了多种预定义类型，如 CoerceType、ListType、DurationType 等

## 使用场景
> 用于 Kether 脚本引擎中解析各种类型的参数
> 配合 QuestReader 一起使用，通过 QuestReader 的 next 方法调用 ArgType 的 read 方法
> 用于创建自定义类型解析器，以便在脚本中支持新的数据类型

## 注意事项
> 实现该接口时，需要处理解析失败的情况，并抛出适当的 LocalizedException
> 建议使用 ArgTypes 类中已定义的标准类型，而不是直接实现该接口

## 使用实例
> CoerceType 是 ArgType 的一个实现，用于基本类型的转换
