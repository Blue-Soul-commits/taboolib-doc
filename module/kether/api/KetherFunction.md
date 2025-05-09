# KetherFunction

## 基本信息
- 类名和包路径: taboolib.module.kether.KetherFunction
- 基本用途: 用于解析文本中嵌入的Kether脚本表达式，将其替换为执行结果
- 类型: 单例对象(object)
- 所属模块: kether

## 类结构
### 公开静态字段
> reader: VariableReader -> 用于读取和替换文本中变量的工具实例

### 公开静态方法
> parse(input: List<String>, options: ScriptOptions = ScriptOptions()): List<String> -> 解析字符串列表中的Kether表达式
> parse(input: String, options: ScriptOptions = ScriptOptions()): String -> 解析字符串中的Kether表达式
> parse(input: List<String>, cacheScript: Boolean, namespace: List<String>, cache: KetherShell.Cache, sender: ProxyCommandSender?, vars: KetherShell.VariableMap?, context: ScriptContext.() -> Unit): List<String> -> [已废弃] 解析字符串列表中Kether表达式的旧方法
> parse(input: String, cacheScript: Boolean, namespace: List<String>, cache: KetherShell.Cache, sender: ProxyCommandSender?, vars: KetherShell.VariableMap?, context: ScriptContext.() -> Unit): String -> [已废弃] 解析字符串中Kether表达式的旧方法

### 类内可被访问字段
> 无

### 类方法
> 无

## 实现细节
- KetherFunction用于解析包含Kether脚本表达式的文本，并将表达式替换为执行结果
- 使用VariableReader来识别和替换文本中的嵌套变量
- 默认使用双大括号("{{" 和 "}}") 作为Kether表达式的标识符
- 新版API使用ScriptOptions类封装所有执行选项，提供更好的可扩展性
- 支持沙盒模式执行，可以捕获脚本执行中的错误
- 借助KetherShell执行实际的脚本解析和运行
- 使用getNow(null)直接获取异步结果，确保字符串替换的同步执行

## 使用场景
> 在文本内容中嵌入动态的Kether脚本表达式
> 创建具有高度定制性的消息模板
> 在配置文件中支持动态脚本逻辑，无需修改代码
> 实现跨模块的文本动态化功能

## 注意事项
> 旧版parse方法已被废弃，建议使用新版ScriptOptions-based的API
> 脚本执行是同步的(使用getNow)，可能会阻塞当前线程
> 在沙盒模式下，如果脚本执行出错，会返回"ERROR"字符串
> 用于解析的VariableReader默认使用双大括号作为边界，可能与其他模板系统冲突

