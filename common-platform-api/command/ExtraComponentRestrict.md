# ExtraComponentRestrict

## 基本信息
- 类名和包路径: taboolib.common.platform.command.ExtraComponentRestrict
- 基本用途: 提供命令组件的类型约束扩展函数，用于限制命令参数的数据类型
- 类型: Kotlin 文件（包含扩展函数）
- 所属模块: TabooLib 平台命令模块

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> restrictInt(): CommandComponentDynamic -> 创建整数类型参数约束
> restrictDouble(): CommandComponentDynamic -> 创建浮点数类型参数约束
> restrictBoolean(): CommandComponentDynamic -> 创建布尔类型参数约束

### 类内可被访问字段
> 无类内可被访问字段（文件级扩展函数）

### 类方法
> 无类方法（文件级扩展函数）

## 实现细节
- 所有函数都是 CommandComponentDynamic 的扩展函数，返回 CommandComponentDynamic 类型，支持链式调用
- restrictInt 函数使用 toIntOrNull 方法验证参数是否可以转换为整数
- restrictDouble 函数使用 toDoubleOrNull 方法验证参数是否可以转换为浮点数
- restrictBoolean 函数使用 toBooleanStrictOrNull 方法验证参数是否可以转换为布尔值
- 所有函数都通过调用 restrict 方法创建约束，使用 ProxyCommandSender 作为发送者类型
- 约束函数不关心发送者和上下文，只验证参数字符串是否符合特定类型

## 使用场景
> 限制命令参数必须是特定的数据类型
> 与 ExtraComponent 中的函数配合使用，为动态参数添加类型约束
> 在自定义命令组件时手动添加类型约束
> 防止用户输入无效的参数值，提高命令的健壮性

## 注意事项
> restrictInt 只接受整数格式，不接受小数或其他格式
> restrictDouble 接受整数和小数格式
> restrictBoolean 只接受严格的布尔值表示（true/false），不接受 1/0 或其他表示
> 这些约束函数会覆盖之前设置的约束或建议
> 在 ExtraComponent 中的 int、decimal、bool 等函数内部已经使用了这些约束函数
> 如果同时设置了建议（suggestion），约束可能会被覆盖，因为建议和约束是互斥的