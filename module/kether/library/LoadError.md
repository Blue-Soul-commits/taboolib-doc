# LoadError

## 基本信息
- 类名和包路径: taboolib.library.kether.LoadError
- 基本用途: 定义 Kether 脚本解析过程中可能出现的错误类型
- 类型: 枚举
- 所属模块: minecraft-kether

## 类结构
### 公开静态字段
> STRING_NOT_CLOSE -> 字符串没有匹配的结束符
> NOT_MATCH -> 输入与预期不匹配
> UNKNOWN_ACTION -> 未知动作
> NOT_DURATION -> 无效的时间段格式
> EOF -> 文件结束（End of File）
> BLOCK_ERROR -> 脚本块错误
> UNHANDLED -> 未处理的异常

### 公开静态方法
> 无

### 类内可被访问字段
> 无

### 类方法
> create(args: Object...): LocalizedException -> 创建一个包含当前错误类型的本地化异常

## 实现细节
- LoadError 是一个枚举类，代表了 Kether 脚本解析过程中的各种错误类型
- 每种错误类型都可以通过 create 方法生成对应的 LocalizedException 实例
- create 方法会自动将错误枚举名转换为对应的本地化消息键（例如 STRING_NOT_CLOSE 转换为 "load-error.string-not-close"）
- 错误消息的实际文本定义在 kether.yml 资源文件中

## 使用场景
> 在 Kether 脚本解析器中标识不同类型的错误
> 在解析失败时抛出特定类型的异常
> 为错误提供本地化的错误消息
> 在 DurationType 等类型转换器中验证输入格式

## 注意事项
> 使用 create 方法时传入的参数会作为错误消息中的占位符参数
> 错误消息的文本定义在 kether.yml 文件中，支持参数占位符如 {0}, {1} 等
> LoadError 通常与 LocalizedException 一起使用，用于提供更具体的错误信息
