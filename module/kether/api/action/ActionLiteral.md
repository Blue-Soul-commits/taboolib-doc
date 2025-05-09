# ActionLiteral

## 基本信息
- 类名和包路径: taboolib.module.kether.action.ActionLiteral
- 基本用途: Kether脚本引擎中的字面量动作，用于表示和返回常量值
- 类型: 类
- 所属模块: kether

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> parser(): QuestActionParser -> 返回用于解析字面量动作的解析器

### 类内可被访问字段
> value: Any -> 存储字面量的值
> isMisspelled: Boolean -> 标记该字面量是否因拼写错误而生成，默认为false

### 类方法
> constructor(value: Any) -> 使用任意类型值创建字面量动作
> constructor(value: String) -> 使用字符串值创建字面量动作
> constructor(value: String, misspelled: Boolean) -> 使用字符串值和拼写错误标记创建字面量动作
> process(frame: QuestContext.Frame): CompletableFuture<T> -> 处理字面量动作，直接返回已完成的future，值为字面量的值

## 实现细节
- ActionLiteral类实现了QuestAction<T>接口，是Kether脚本中最基础的动作类型
- 使用泛型T表示返回值类型，但在process方法中直接进行了类型转换(value as T)
- 提供了三个构造函数，用于创建不同类型和标记的字面量
- isMisspelled属性用于标记该字面量是否因脚本中的拼写错误而自动生成
- process方法非常简单，仅返回包含字面量值的已完成future
- companion object中提供了parser静态方法，创建一个解析器读取下一个标记作为字面量值

## 使用场景
> 在Kether脚本中表示常量值，如数字、字符串等
> 作为其他复杂动作的参数
> 在容错解析时，将未识别的标记视为字面量
> 在宽容模式下，允许省略literal关键字直接使用值

## 注意事项
> process方法中进行了无检查的类型转换(value as T)，可能会在运行时引发ClassCastException
> isMisspelled属性只能设置一次，通过private set限制
> parser方法返回的解析器只会读取下一个标记，不会处理引号或其他特殊语法
> 在Kether.isAllowToleranceParser为true时，许多未识别的标记可能被解析为ActionLiteral