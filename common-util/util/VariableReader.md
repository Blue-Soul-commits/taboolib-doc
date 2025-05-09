# VariableReader

## 基本信息
- 类名和包路径: taboolib.common.util.VariableReader
- 基本用途: 解析和处理包含变量的字符串模板
- 类型: Kotlin类
- 所属模块: common-util

## 类结构
> VariableReader(start: String = "{{", end: String = "}}") -> 主类，处理变量替换
> Part(text: String, isVariable: Boolean) -> 数据类，表示解析后的文本片段

## 方法
> replaceNested(source: String, transfer: String.() -> String): String -> 替换嵌套变量
> readToFlatten(source: String): List<Part> -> 将字符串解析为文本片段列表
> format(str: String): String -> 处理转义字符
> indexOf(source: String, str: String, start: Int): Int -> 查找非转义的子字符串位置
> lastIndexOf(source: String, str: String, start: Int): Int -> 从后向前查找非转义的子字符串位置

## 实现细节
### 构造函数
- 允许自定义变量的开始和结束标记，默认为"{{"和"}}"
- 这使得类可以适应不同的模板语法

### replaceNested
- 处理嵌套变量，从内到外替换
- 使用`indexOf`和`lastIndexOf`查找最内层的变量
- 对每个变量应用`transfer`函数进行转换
- 递归处理直到没有变量为止
- 最后对整个字符串应用`format`处理转义字符

### readToFlatten
- 将字符串解析为文本片段列表
- 每个片段标记为变量或普通文本
- 按顺序处理所有变量
- 对所有片段应用`format`处理转义字符

### format
- 处理转义字符，将"\{{"转换为"{{"，"\}}"转换为"}}"
- 使用`buildString`优化字符串构建
- 通过字符级别的解析实现，而非使用正则表达式

### indexOf/lastIndexOf
- 查找非转义的子字符串位置
- 忽略被反斜杠"\"转义的匹配项
- 支持指定起始位置的搜索

## 使用场景
> 模板引擎实现
> 配置文件中的变量替换
> 消息格式化
> 文本处理和转换
> 支持嵌套变量的场景

## 注意事项
> 变量可以嵌套，内层变量会先被处理
> 使用反斜杠"\"可以转义变量标记
> `replaceNested`方法需要提供变量处理函数
> `readToFlatten`方法适用于需要分别处理变量和文本的场景
> 默认使用"{{"和"}}"作为变量标记，但可以自定义
