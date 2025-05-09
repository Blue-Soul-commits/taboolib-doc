# LocalizedException

## 基本信息
- 类名和包路径: taboolib.library.kether.LocalizedException
- 基本用途: 表示 Kether 脚本解析和执行过程中的本地化异常信息
- 类型: 异常类
- 所属模块: minecraft-kether

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> of(error: LoadError, node: String, params: Object...): LocalizedException -> 创建一个包含特定错误类型的本地化异常
> of(node: String, params: Object...): LocalizedException -> 创建默认错误类型(UNKNOWN_ACTION)的本地化异常
> supply(node: String, params: Object...): Supplier<LocalizedException> -> 创建返回本地化异常的供应者
> batch(exceptions: LocalizedException...): LocalizedException -> 批量合并多个本地化异常

### 类内可被访问字段
> error: LoadError -> 异常关联的错误类型
> node: String -> 本地化消息的节点路径
> params: Object[] -> 本地化消息的参数

### 类方法
> LocalizedException(error: LoadError, node: String, params: Object[]) -> 构造函数
> getError(): LoadError -> 获取异常关联的错误类型
> getNode(): String -> 获取本地化消息的节点路径
> getParams(): Object[] -> 获取本地化消息的参数
> getMessage(): String -> 获取已本地化的错误消息
> getLocalizedMessage(): String -> 获取已本地化的错误消息
> stream(): Stream<LocalizedException> -> 将异常转换为流
> then(e: LocalizedException): LocalizedException -> 将当前异常与另一个异常连接

## 实现细节
- LocalizedException 继承自 RuntimeException，用于处理 Kether 脚本中的错误
- 错误消息会根据当前语言环境进行本地化，使用 QuestService.instance().getLocalizedText() 方法
- 本地化消息存储在 kether.yml 资源文件中，以节点路径为键
- 支持消息参数，使用 {0}, {1} 等占位符表示
- 实现了 Concat 内部类，用于批量合并多个异常，提供更详细的错误报告

## 使用场景
> 在 Kether 脚本解析过程中标识和报告错误
> 提供多语言支持的错误消息
> 链接多个相关的错误，形成更详细的错误报告
> 与 LoadError 枚举配合使用，标识不同类型的错误

## 注意事项
> 使用 then() 方法可以将多个异常链接起来，以提供更详细的错误上下文
> 节点路径通常以 "load-error." 开头，后面跟着错误类型的小写和用连字符分隔的形式
> 必须确保 QuestService 实例已初始化，否则无法获取本地化消息
