# ParserHolder

## 基本信息
- 类名和包路径: taboolib.module.kether.ParserHolder
- 基本用途: Kether脚本引擎的解析器工具类，提供各种类型的解析器和辅助函数
- 类型: 单例对象(object)
- 所属模块: kether

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> any(): Parser<Any?> -> 创建解析任意类型的解析器
> anyAsList(): Parser<MutableList<Any?>> -> 创建解析任意类型并转换为列表的解析器
> originList(): Parser<MutableList<Any?>> -> 创建解析原始列表的解析器
> type<T>(): Parser<T> -> 创建解析特定类型的解析器
> action(): Parser<ParsedAction<*>> -> 创建解析动作的解析器
> actionList(): Parser<MutableList<ParsedAction<*>>> -> 创建解析动作列表的解析器
> symbol(): Parser<String> -> 创建解析固定文本的解析器
> text(): Parser<String> -> 创建解析文本的解析器
> int(): Parser<Int> -> 创建解析整数的解析器
> long(): Parser<Long> -> 创建解析长整数的解析器
> double(): Parser<Double> -> 创建解析双精度浮点数的解析器
> float(): Parser<Float> -> 创建解析浮点数的解析器
> bool(): Parser<Boolean> -> 创建解析布尔值的解析器
> now<T>(action: ScriptFrame.() -> T): Action<T> -> 创建立即执行并返回结果的动作
> future<T>(action: ScriptFrame.() -> CompletableFuture<T>): Action<T> -> 创建执行并返回Future的动作
> completedFuture<T>(value: T): CompletableFuture<T> -> 创建已完成的Future

### 类内可被访问字段
> 无

### 类方法
> Parser<A>.and(b: Parser<B>): Parser<Pair<A, B>> -> 扩展函数，组合两个解析器
> Parser<A>.and(b: Parser<B>, c: Parser<C>): Parser<Triple<A, B, C>> -> 扩展函数，组合三个解析器
> Parser<A>.option(): Parser<A?> -> 扩展函数，使解析器变为可选
> Parser<A?>.defaultsTo(value: A): Parser<A> -> 扩展函数，为可空解析器提供默认值
> command<A>(vararg s: String, then: Parser<A>): Parser<A> -> 创建子命令解析器

## 实现细节
- ParserHolder是一个工具类，提供了丰富的解析器创建和组合功能
- 使用泛型和扩展函数实现了灵活的解析器组合和转换
- any()解析器是最基础的解析器，大多数其他解析器都基于它构建
- 数值类型解析器(如int()、double())优先尝试直接解析，失败时尝试转换任意类型
- 支持多种解析器组合方式，如and()用于并列参数，option()用于可选参数
- 提供了now()和future()函数，简化动作执行逻辑的实现
- 对非法或无法解析的输入提供了多种容错和默认值机制

## 使用场景
> 在Kether脚本动作解析器中创建参数解析规则
> 组合多个解析器创建复杂的参数解析链
> 实现动作解析器时处理不同类型的输入参数
> 简化异步动作的实现，通过future和now函数

## 注意事项
> 解析器执行顺序很重要，会影响脚本解析结果
> 数值类型解析可能导致类型转换异常，应当妥善处理
> anyAsList()使用了未检查的类型转换，可能导致ClassCastException
> 使用option()和defaultsTo()可以提高脚本的容错性
