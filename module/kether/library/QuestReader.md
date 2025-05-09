# QuestReader

## 基本信息
- 类名和包路径: taboolib.library.kether.QuestReader
- 基本用途: 解析 Kether 脚本文本，提供词法和语法分析功能
- 类型: 接口
- 所属模块: minecraft-kether

## 类结构
### 接口方法
> peek(): char -> 获取当前位置的字符，不移动指针
> peek(int n): char -> 获取当前位置向后第 n 个字符，不移动指针
> getIndex(): int -> 获取当前指针位置
> getMark(): int -> 获取当前标记位置
> hasNext(): boolean -> 检查是否还有更多内容
> nextToken(): String -> 获取下一个标记（通常是一个词）
> mark(): void -> 设置当前位置的标记
> reset(): void -> 将指针重置到上一个标记位置
> nextAction(): ParsedAction<T> -> 解析下一个动作
> nextAction(String namespace): ParsedAction<T> -> 在指定命名空间下解析下一个动作
> expect(String value): void -> 期望下一个标记等于指定值，否则抛出异常

### 默认方法
> nextInt(): int -> 解析下一个整数
> nextLong(): long -> 解析下一个长整数
> nextDouble(): double -> 解析下一个双精度浮点数
> next(ArgType<T> argType): T -> 使用指定的参数类型解析下一个值
> nextParsedAction(): ParsedAction<?> -> 解析下一个动作
> nextParsedAction(String namespace): ParsedAction<?> -> 在指定命名空间下解析下一个动作

## 实现细节
- 主要实现类是 SimpleReader，继承自 AbstractStringReader 并实现 QuestReader 接口
- SimpleReader 负责处理脚本字符串并提取各种语法元素
- 解析过程中，Reader 维护一个指针位置和标记位置，用于在脚本中导航
- 遇到 '{' 字符时，会解析为匿名代码块
- 遇到 '&' 字符时，会解析为变量引用 (ActionGet)
- 遇到 '*' 字符时，会解析为字面量 (ActionLiteral)
- 其他标记会尝试在注册表中查找对应的动作解析器

## 使用场景
> 解析 Kether 脚本文本为可执行的动作序列
> 在 QuestActionParser 的 resolve 方法中用于读取动作参数
> 支持自定义参数类型解析，通过 ArgType 机制

## 注意事项
> 解析过程中可能抛出 LocalizedException 异常，特别是 LoadError 类型的错误
> 命名空间机制用于解析不同来源的动作，必要时需要正确指定
> SimpleReader 实现中默认会添加 "kether" 命名空间
