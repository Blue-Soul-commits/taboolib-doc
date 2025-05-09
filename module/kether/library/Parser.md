# Parser

## 基本信息
- 类名和包路径: taboolib.library.kether.Parser
- 基本用途: 提供函数式和组合式的脚本解析功能，支持 Kether 脚本语言的语法和语义分析
- 类型: 泛型类
- 所属模块: minecraft-kether

## 类结构
### 公开静态字段
> Mu: 类 -> 内部标记类，用于函数式类型系统

### 公开静态方法
> unbox(box: App<Parser.Mu, T>): Parser<T> -> 从 App 接口类型中解包出 Parser 对象
> point(value: T): Parser<T> -> 创建一个包含给定值的 Parser 对象
> of(parser: Function<QuestReader, T>): Parser<T> -> 通过函数创建 Parser 对象
> frame(parser: Function<QuestReader, Action<T>>): Parser<T> -> 通过帧处理函数创建 Parser 对象
> create(builder: Function<Instance, App<Mu, Action<A>>>): QuestActionParser -> 创建 QuestActionParser 对象
> build(fa: App<Mu, Action<A>>): QuestActionParser -> 构建 QuestActionParser 对象
> instance(): Instance -> 获取单例 Instance 对象

### 类内可被访问字段
> reader: Function<QuestReader, Action<T>> -> 解析函数，将 QuestReader 转换为动作

### 类方法
> orElse(other: Parser<T>): Parser<T> -> 如果当前解析器失败，则尝试使用其他解析器
> either(parser: Parser<B>): Parser<Either<T, B>> -> 创建一个可以解析两种类型之一的解析器
> optional(): Parser<Optional<T>> -> 创建一个可选解析器，解析失败时返回空 Optional
> listOf(): Parser<List<T>> -> 创建一个列表解析器，解析方括号包围的元素列表
> map(func: Function<T, R>): Parser<R> -> 映射结果到新类型
> fold(fb: Parser<B>, func: BiFunction<T, B, R>): Parser<R> -> 组合两个解析器的结果
> fold(fb: Parser<B>, fc: Parser<C>, func: Function3<T, B, C, R>): Parser<R> -> 组合三个解析器的结果

## 实现细节
- 使用函数式编程和组合子模式设计，支持解析器组合和转换
- 内部类 Action 定义了动作执行的接口，是脚本运行时的基本单位
- 使用 Applicative 函子模式实现函数应用和组合
- 支持多种解析组合方式，如条件选择、序列组合、错误恢复等
- 提供泛型类型安全，确保解析结果类型与预期一致
- Instance 内部类是 Applicative 接口的实现，提供高阶函数操作

## 使用场景
> 在 Kether 脚本引擎中定义和组合语法解析规则
> 通过 combinationParser 构建复杂的命令解析器
> 在脚本动作中使用 ParserHolder 提供的扩展功能解析参数
> 实现自定义脚本语言功能，如条件判断、循环、变量操作等

## 注意事项
> 使用 Parser 需要了解函数式编程和组合子模式
> 解析失败会抛出异常，通常需要使用 orElse 或 optional 处理错误情况
> 在复杂解析逻辑中，应合理组合基本解析器以提高可维护性
> 使用 combinationParser 时需要在 ParserHolder 上下文中操作

