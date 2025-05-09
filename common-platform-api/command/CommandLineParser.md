# CommandLineParser

## 基本信息
- 类名和包路径: taboolib.common.platform.command.CommandLineParser
- 基本用途: 解析命令行字符串，提取选项和参数
- 类型: 工具类
- 所属模块: TabooLib 平台命令模块

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> line: String -> 待解析的命令行字符串
> escapes: Array<Char> -> 支持转义的字符数组 ['\'', '\"', '=', '-', ':', '\\']
> options: MutableMap<String, String> -> 解析后的选项映射
> args: MutableList<String> -> 解析后的参数列表
> value: StringBuilder -> 当前正在构建的文本块
> quote: Boolean -> 当前是否在引号内
> option: Boolean -> 当前是否在处理选项
> optionName: StringBuilder -> 当前正在构建的选项名称

### 类方法
> parse(): CommandLineParser -> 解析命令行字符串，返回解析器自身
> close(): Unit -> 结束当前解析状态，处理剩余内容
> closeValue(): Unit -> 结束参数解析，将当前值添加到参数列表
> closeOption(): Unit -> 结束选项解析，将当前选项添加到选项映射
> StringBuilder.plusAssign(c: Char): Unit -> 重载运算符，向StringBuilder添加字符
> StringBuilder.plusAssign(s: String): Unit -> 重载运算符，向StringBuilder添加字符串
> StringBuilder.plusAssign(s: StringBuilder): Unit -> 重载运算符，向StringBuilder添加另一个StringBuilder内容

## 实现细节
- 使用状态机模式逐字符解析命令行
- 支持选项（以'-'开头）和普通参数的区分
- 支持使用单引号或双引号包裹含空格的参数
- 支持使用反斜杠(\)转义特殊字符
- 支持选项使用等号(=)或冒号(:)赋值
- 通过重载运算符简化StringBuilder的操作

## 使用场景
> 解析复杂的命令行输入，如带选项和引号的命令
> 在命令系统中提取命令参数和选项
> 支持新的命令解析格式，提供更灵活的命令输入方式

## 注意事项
> 选项必须以'-'开头
> 引号（单引号或双引号）必须成对出现
> 转义字符仅对特定字符有效（'\'', '\"', '=', '-', ':', '\\'）
> 选项可以没有值，此时在options中对应的值为空字符串