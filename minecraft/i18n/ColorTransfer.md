# ColorTransfer
## 基本信息
- 类名和包路径: taboolib.module.lang.ColorTransfer
- 基本用途: 实现TextTransfer接口，提供文本颜色代码转换功能
- 类型: 单例对象(object)
- 所属模块: minecraft-i18n

## 类结构
### 公开静态字段
> isSupported: Boolean -> 指示颜色模块是否可用的标志

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> 无额外字段

### 类方法
> translate(sender: ProxyCommandSender, source: String, vararg args: Any): String -> 将文本中的颜色代码转换为可显示的颜色

## 实现细节
- ColorTransfer是一个单例对象，实现了TextTransfer接口
- 通过isSupported字段检测颜色模块是否可用，使用try-catch捕获可能的NoClassDefFoundError
- translate方法简单调用String.colored()扩展函数处理颜色代码
- colored()扩展函数来自taboolib.module.chat模块，内部使用HexColor.translate实现
- 不关心sender和args参数，仅对source文本进行处理
- 作为TextTransfer的实现，可以被添加到Language.textTransfer列表中

## 使用场景
> 在TabooLib国际化系统中，作为默认的颜色处理器
> 将配置文件中的颜色代码(&、§、&{})转换为游戏中可显示的颜色
> 与其他TextTransfer实现配合，构建完整的文本处理链
> 在不需要复杂颜色处理逻辑的场景中，提供简单的颜色转换功能
> 支持HexColor中定义的所有颜色格式，包括RGB、HEX和命名颜色

## 注意事项
> isSupported字段在初始化时确定，如果缺少必要的类(如HexColor)，将设置为false
> 当isSupported为false时，translate方法仍会调用colored()，可能导致运行时错误
> 不处理sender特定的颜色偏好，对所有接收者应用相同的颜色处理
> 不使用args参数，忽略了可能的自定义颜色处理选项
> 依赖taboolib.module.chat模块，确保该模块可用
