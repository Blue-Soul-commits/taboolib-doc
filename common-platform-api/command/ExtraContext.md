# ExtraContext

## 基本信息
- 类名和包路径: taboolib.common.platform.command.ExtraContext
- 基本用途: 提供命令上下文的扩展函数，用于从命令参数中获取并转换基本数据类型
- 类型: Kotlin 文件（包含扩展函数）
- 所属模块: TabooLib 平台命令模块

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> int(id: String): Int -> 获取并转换为整型参数
> intOrNull(id: String): Int? -> 获取并尝试转换为整型参数，可能返回 null
> double(id: String): Double -> 获取并转换为双精度浮点型参数
> doubleOrNull(id: String): Double? -> 获取并尝试转换为双精度浮点型参数，可能返回 null
> float(id: String): Float -> 获取并转换为单精度浮点型参数
> floatOrNull(id: String): Float? -> 获取并尝试转换为单精度浮点型参数，可能返回 null
> bool(id: String): Boolean -> 获取并转换为布尔值参数
> boolOrNull(id: String): Boolean? -> 获取并尝试转换为布尔值参数，可能返回 null

### 类内可被访问字段
> 无类内可被访问字段（文件级扩展函数）

### 类方法
> 无类方法（文件级扩展函数）

## 实现细节
- 所有函数都是 CommandContext<T> 的泛型扩展函数，适用于任何类型的命令上下文
- int 和 intOrNull 函数使用 toInt 和 toIntOrNull 方法转换参数
- double 和 doubleOrNull 函数使用 toDouble 和 toDoubleOrNull 方法转换参数
- float 和 floatOrNull 函数使用 toFloat 和 toFloatOrNull 方法转换参数
- bool 和 boolOrNull 函数接受多种布尔值表示："true"、"t"、"1"（不区分大小写）
- 非 Null 版本的函数在参数不存在或转换失败时会抛出异常
- Null 版本的函数在参数不存在或转换失败时会返回 null
- 所有函数都通过调用 CommandContext 的 get 或 getOrNull 方法获取原始参数值

## 使用场景
> 在命令执行器中获取并转换命令参数
> 简化命令参数的类型转换，避免重复的转换代码
> 处理可能缺失或格式错误的参数
> 与 ExtraComponent 中的函数配合使用，实现类型安全的命令参数处理
> 在复杂命令中获取多个不同类型的参数

## 注意事项
> int、double、float 和 bool 函数在参数不存在或转换失败时会抛出异常
> intOrNull、doubleOrNull、floatOrNull 和 boolOrNull 函数在参数不存在或转换失败时会返回 null
> bool 函数接受 "true"、"t"、"1" 作为真值，其他值视为假
> 参数名称 id 应该与命令定义时使用的参数名称一致
> 这些函数通常与 ExtraComponent 中的类型节点函数配合使用
