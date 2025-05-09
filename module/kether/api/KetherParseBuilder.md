# KetherParseBuilder

## 基本信息
- 类名和包路径: taboolib.module.kether.KetherParseBuilder (文件名，非类名)
- 基本用途: Kether脚本解析器的构建工具，提供DSL风格的语法和便捷函数
- 类型: 工具函数集合和DSL类
- 所属模块: kether

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> literalAction(any: Any): ParsedAction<*> -> 创建一个包含字面量的已解析动作
> expects(vararg args: String): String -> QuestReader的扩展函数，期望下一个标记匹配给定的参数之一
> switch(func: ExpectDSL.() -> Unit): ScriptAction<*> -> QuestReader的扩展函数，创建条件分支解析结构
> actionNow(name: String = "actionNow", func: QuestContext.Frame.() -> Any?): ScriptAction<Any?> -> 创建同步执行的动作
> actionTake(name: String = "actionTake", func: QuestContext.Frame.() -> CompletableFuture<*>): ScriptAction<Any?> -> 创建接管异步操作的动作
> actionFuture(name: String = "actionFuture", func: QuestContext.Frame.(CompletableFuture<Any?>) -> Any?): ScriptAction<Any?> -> 创建使用Future的动作

### 类内可被访问字段
> 无

### 类方法
> 无（主要提供静态函数和DSL类）

## 实现细节
- 文件提供了一系列实用函数，简化Kether脚本解析和动作创建
- literalAction函数创建一个包装了字面量的ParsedAction
- expects扩展函数验证下一个标记是否匹配预期，不匹配时抛出异常
- switch扩展函数实现了一个类似switch语句的DSL，支持多条件分支
- 提供了三种创建动作的函数：actionNow用于同步操作，actionTake用于接管已有的异步操作，actionFuture用于创建新的异步操作
- ExpectDSL类提供了声明式的条件分支语法，支持case和other方法

## 使用场景
> 实现复杂的Kether脚本解析器
> 创建简单的同步或异步脚本动作
> 构建多条件分支的解析逻辑
> 简化重复的解析代码模式

## 注意事项
> switch函数会在解析失败时重置读取位置，可能影响性能
> actionTake函数使用了不安全的类型转换(as CompletableFuture<Any?>)
> 动作的toString方法返回自定义名称，便于调试
> ExpectDSL的other方法可以返回null，表示无法处理的情况
> expects函数在不匹配时抛出的异常包含了期望值和实际值
