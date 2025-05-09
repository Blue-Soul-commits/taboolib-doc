# ExtraContextOption 
## 基本信息 
- 类名和包路径: taboolib.common.platform.command.ExtraContextOption
- 基本用途: 为 CommandContext 类提供扩展函数，用于获取命令选项并转换为不同的数据类型
- 类型: Kotlin 扩展函数文件
- 所属模块: common-platform-api

## 类结构 
### 公开静态字段 
> 无静态字段

### 公开静态方法 
> optionInt(vararg id: String): Int -> 获取选项并转换为整形，如果选项不存在则抛出异常
> optionIntOrNull(vararg id: String): Int? -> 获取选项并转换为整形，如果选项不存在则返回 null
> optionDouble(vararg id: String): Double -> 获取选项并转换为双精度浮点数，如果选项不存在则抛出异常
> optionDoubleOrNull(vararg id: String): Double? -> 获取选项并转换为双精度浮点数，如果选项不存在则返回 null
> optionFloat(vararg id: String): Float -> 获取选项并转换为单精度浮点数，如果选项不存在则抛出异常
> optionFloatOrNull(vararg id: String): Float? -> 获取选项并转换为单精度浮点数，如果选项不存在则返回 null
> optionBoolean(vararg id: String): Boolean -> 获取选项并转换为布尔值，如果选项不存在则抛出异常
> optionBooleanOrNull(vararg id: String): Boolean? -> 获取选项并转换为布尔值，如果选项不存在则返回 null

### 类内可被访问字段 
> 无类内字段（扩展函数文件）

### 类方法
> 无类方法（扩展函数文件）

## 实现细节
- 所有扩展函数都是 CommandContext 类的扩展，用于处理命令选项
- 每个扩展函数都有两个版本：一个在选项不存在时抛出异常，另一个在选项不存在时返回 null
- 布尔值转换支持 "true"、"t"（不区分大小写）作为 true 值
- 所有函数都依赖于 CommandContext 类的 option 方法来获取原始选项值
- 这些扩展函数只能在使用新命令解析器（newParser=true）的命令中使用

## 使用场景 
> 在命令处理中获取并转换命令选项的类型
> 处理带有选项的复杂命令，如 "/command -option value"
> 在命令执行器中安全地获取并转换用户输入的选项值

## 注意事项 
> 所有非 Null 版本的方法在选项不存在时会抛出 IllegalStateException 异常
> 使用这些扩展函数的命令必须启用新的命令解析器（newParser=true），否则会抛出异常
> 类型转换可能会因为输入格式不正确而抛出异常（如将非数字字符串转换为整数）
