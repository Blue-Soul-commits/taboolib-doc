# AbstractStringReader

## 基本信息
- 类名和包路径: taboolib.library.kether.AbstractStringReader
- 基本用途: 提供基础的字符串解析功能，作为脚本解析器的基础工具类
- 类型: 抽象类
- 所属模块: minecraft-kether

## 类结构
### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> content: char[] -> 存储待解析的字符内容
> index: int -> 当前解析位置的索引
> mark: int -> 标记的位置索引

### 类方法
> AbstractStringReader(content: char[]) -> 使用指定字符数组创建解析器
> AbstractStringReader(content: char[], index: int, mark: int) -> 使用指定字符数组、索引和标记创建解析器
> peek(): char -> 获取当前索引位置的字符，如果到达末尾则抛出 EOF 异常
> peek(n: int): char -> 获取当前索引位置后 n 个位置的字符，如果到达末尾则抛出 EOF 异常
> hasNext(): boolean -> 跳过空白字符后，检查是否还有更多内容
> mark(): void -> 将当前索引位置标记为 mark
> reset(): void -> 将索引重置为 mark 的位置
> nextToken(): String -> 读取下一个标记（非空白字符序列）
> skip(n: int): void -> 跳过 n 个字符
> skipBlank(): void -> 跳过空白字符和注释（//开头的行）
> expect(value: String): void -> 期望下一个标记匹配指定值，否则抛出异常
> failExpect(expect: String, got: String): void -> 抛出不匹配异常
> getContent(): char[] -> 获取内容字符数组
> getIndex(): int -> 获取当前索引位置
> getMark(): int -> 获取当前标记位置
> getRemain(): String -> 获取从当前索引位置到末尾的剩余字符串

## 实现细节
- 提供一个基础的字符串解析器，支持逐字符读取、标记位置和重置功能
- 支持跳过空白字符和行注释（以 // 开头的注释）
- 实现了简单的词法分析功能，能够按照空白字符分割读取标记
- 提供错误处理机制，当解析到达末尾或期望值不匹配时抛出异常

## 使用场景
> 作为 Kether 脚本解析器的基础，被 SimpleReader 等具体的解析器继承使用
> 在需要对字符串内容进行逐字符解析和词法分析的场景下使用

## 注意事项
> 该类是抽象类，需要被具体类继承实现完整功能
> 类中的解析方法在遇到文件结束或格式错误时会抛出 LoadError 相关异常
> 使用 mark() 和 reset() 方法可以实现回溯功能，对于需要前瞻的解析很有用
