# CommandComponentDynamic

## 基本信息
- 类名和包路径: taboolib.common.platform.command.component.CommandComponentDynamic
- 基本用途: 动态命令组件，用于处理变量参数和提供参数补全
- 类型: 类（继承自 CommandComponent）
- 所属模块: TabooLib 平台命令组件模块

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> comment: String -> 参数注释/标识符
> commandRestrict: CommandRestrict<*>? -> 参数约束处理器
> commandSuggestion: CommandSuggestion<*>? -> 参数补全建议处理器

### 类方法
> restrict<T>(bind: Class<T>, function: (sender: T, context: CommandContext<T>, argument: String) -> Boolean): CommandComponentDynamic -> 设置参数约束
> suggestion<T>(bind: Class<T>, uncheck: Boolean, function: (sender: T, context: CommandContext<T>) -> List<String>?): CommandComponentDynamic -> 设置参数补全建议
> restrict<T>(function: (sender: T, context: CommandContext<T>, argument: String) -> Boolean): CommandComponentDynamic -> 设置参数约束（使用泛型推断）
> suggestion<T>(uncheck: Boolean, function: (sender: T, context: CommandContext<T>) -> List<String>?): CommandComponentDynamic -> 设置参数补全建议（使用泛型推断）
> suggestionUncheck<T>(function: (sender: T, context: CommandContext<T>) -> List<String>?): CommandComponentDynamic -> 设置不检查的参数补全建议
> removeRestrict(): CommandComponentDynamic -> 移除参数约束
> removeSuggestion(): CommandComponentDynamic -> 移除参数补全建议
> toString(): String -> 返回组件的字符串表示

## 实现细节
- 继承自 CommandComponent，专门用于处理动态参数
- 支持参数约束和参数补全建议功能
- 设置约束时会自动清除建议，设置建议时会自动清除约束
- 使用泛型设计，支持不同类型的命令发送者
- 提供了带类型推断的内联函数版本，简化使用
- 支持链式调用，所有设置方法都返回组件本身

## 使用场景
> 处理命令中的变量参数，如玩家名、物品ID等
> 提供参数输入约束，限制用户输入的有效性
> 提供参数补全建议，帮助用户输入正确的参数

## 注意事项
> comment 字段用于在命令上下文中标识该参数
> 约束和建议是互斥的，设置一个会清除另一个
> uncheck 参数为 true 时，即使输入不在建议列表中也会被接受
> 使用 suggestionUncheck 方法等同于 suggestion(uncheck = true)