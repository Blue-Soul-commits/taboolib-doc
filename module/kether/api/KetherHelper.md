    # KetherHelper

## 基本信息
- 类名和包路径: taboolib.module.kether.KetherHelper (文件名，非类名)
- 基本用途: Kether脚本引擎的辅助函数集合，提供各种实用工具和扩展函数
- 类型: 功能性工具类和扩展函数集合
- 所属模块: kether

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> runKether<T>(el: T? = null, detailError: Boolean = false, function: () -> T): T? -> 运行Kether语句并处理错误
> scriptParser<T>(resolve: (QuestReader) -> QuestAction<T>): ScriptActionParser<T> -> 创建脚本解析器
> combinationParser<T>(builder: ParserHolder.(Instance) -> App<Mu, Action<T>>): ScriptActionParser<T> -> 创建组合解析器

### 类内可被访问字段
> 无

### 类方法
> 无（文件中只包含类型别名和扩展函数）

## 实现细节
- 定义了两个类型别名：Script为Quest的别名，ScriptFrame为QuestContext.Frame的别名
- runKether函数用于安全执行Kether脚本，捕获并打印异常
- scriptParser和combinationParser函数简化了脚本解析器的创建
- 提供了多个String和List<String>的扩展函数，用于解析Kether脚本
- 为ScriptFrame和ScriptContext提供了多个扩展函数，增强功能
- printKetherErrorMessage扩展函数用于格式化并打印Kether错误信息
- inferType扩展函数用于推断字符串的实际数据类型

## 使用场景
> 简化Kether脚本解析器的创建和使用
> 从字符串或字符串列表创建Kether脚本
> 在脚本帧中执行动作和获取上下文信息
> 安全执行Kether代码，提供友好的错误处理
> 处理脚本变量和上下文状态

## 注意事项
> runKether函数会捕获所有异常，可能掩盖某些问题
> parseKetherScript扩展函数生成的脚本ID包含随机UUID，不利于跟踪
> player()扩展函数在sender不是玩家时会抛出错误
> printKetherErrorMessage根据异常类型提供不同的错误提示
> inferType扩展函数尝试将字符串转换为更具体的数据类型
