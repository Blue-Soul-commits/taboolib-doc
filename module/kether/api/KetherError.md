# KetherError

## 基本信息
- 类名和包路径: taboolib.module.kether.KetherError
- 基本用途: 定义Kether脚本模块中的错误类型，用于创建本地化异常
- 类型: 枚举类
- 所属模块: kether

## 类结构
### 公开静态字段
> NOT_SYMBOL -> 表示非符号错误
> NOT_COMMAND_SENDER -> 表示非命令发送者错误
> NOT_EVENT_OPERATOR -> 表示非事件操作者错误
> NOT_EVENT -> 表示非事件错误
> NOT_PLAYER_OPERATOR -> 表示非玩家操作者错误
> NOT_MATERIAL -> 表示非材料错误
> CUSTOM -> 表示自定义错误

### 公开静态方法
> 无

### 类内可被访问字段
> 无

### 类方法
> create(vararg args: Any?): LocalizedException -> 创建一个包含当前错误类型的本地化异常

## 实现细节
- KetherError 是一个枚举类，定义了Kether脚本模块中特定的错误类型
- 通过create方法将错误类型转换为本地化异常实例
- create方法会自动将枚举名转换为小写并用连字符替换下划线，作为本地化消息的键
- 例如：NOT_SYMBOL 会转换为 "load-error.not-symbol"
- 返回的LocalizedException实例包含了本地化消息和传入的参数

## 使用场景
> 在Kether脚本解析和执行过程中标识特定类型的错误
> 提供更具体的错误类型，补充library.kether.LoadError中的基础错误类型
> 用于创建带有上下文的本地化异常信息
> 在Kether脚本的Kotlin部分中处理特定领域的错误情况

## 注意事项
> 错误消息的实际文本需要在语言文件中定义，键格式为"load-error.枚举名小写-连字符形式"
> 使用create方法时传入的参数将作为本地化消息中的占位符参数
> 与library.kether中的LoadError枚举类似，但专注于Kotlin模块中的特定错误类型
> CUSTOM类型可用于创建自定义错误消息，更加灵活
