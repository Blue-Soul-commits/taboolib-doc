# ColorRegex

## 基本信息
- 类名和包路径: taboolib.common5.ColorRegex
- 基本用途: 提供处理 Minecraft 物品 Lore 文本的正则表达式工具，特别是处理带有颜色代码的文本
- 类型: 工具类
- 所属模块: common-legacy-api

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> patternIgnoreColor(regex: String): Pattern -> 将纯文本转换为能忽略颜色代码的正则表达式模式
> stringToRegexIgnoreColor(regex: String): String -> 将纯文本转换为能忽略颜色代码的正则表达式字符串
> stringToRegex(str: String): String -> 将纯文本转换为正则表达式字符串，类似于 Pattern.quote() 但不使用 \Q 和 \E
> stringToRegex(str: String, delimiter: String, ignoreColor: boolean): String -> 将纯文本转换为正则表达式字符串，可在每个字符前添加分隔符，并可选择是否忽略颜色代码

### 类内可被访问字段
> 无类内可被访问字段

### 类方法
> 无非静态方法

## 实现细节
- 使用 StringBuilder 逐字符构建正则表达式，对特殊字符进行转义
- 通过在字符间插入特定模式（如 `(?:§.)*`）来实现忽略颜色代码的功能
- 颜色代码的处理基于 Minecraft 的格式（§ 符号后跟一个字符）
- 支持对正则表达式特殊字符的自动转义，包括 :+*?^$.()\[]

## 使用场景
> 处理 Minecraft 物品 Lore 文本，需要忽略其中的颜色代码进行匹配
> 在物品描述中查找或替换特定文本，而不受颜色代码的影响
> 创建能够匹配带有颜色代码的文本的正则表达式
> 在插件开发中处理带有格式代码的聊天消息或物品描述

## 注意事项
> 该类主要针对 Minecraft 的颜色代码系统（§ 符号），不适用于其他格式的颜色编码
> 生成的正则表达式可能比原始文本复杂得多，可能影响匹配性能
> 使用 ignoreColor 参数时，原文本中的颜色代码将被完全忽略，不会出现在生成的正则表达式中
> 默认情况下，生成的模式是大小写不敏感的（使用了 Pattern.CASE_INSENSITIVE 标志）