# KetherTransfer

## 基本信息
- 类名和包路径: taboolib.module.kether.KetherTransfer
- 基本用途: 实现TextTransfer接口，用于在文本中嵌入并执行Kether脚本
- 类型: 单例对象(object)
- 所属模块: kether

## 类结构
### 公开静态字段
> cacheMap: KetherShell.Cache -> 用于存储解析后的脚本缓存
> namespace: ArrayList<String> -> 存储脚本执行时使用的命名空间列表

### 公开静态方法
> translate(sender: ProxyCommandSender, source: String, vararg args: Any): String -> 将文本中的Kether表达式替换为执行结果

### 类内可被访问字段
> 无

### 类方法
> 无

## 实现细节
- KetherTransfer实现了TextTransfer接口，用于文本本地化系统
- 在translate方法中检测文本是否包含"{{" 标记，这是Kether表达式的标识符
- 如果文本包含Kether表达式，则使用KetherFunction.parse方法解析和执行
- 传入的可变参数args会按照索引顺序转换为arg0、arg1等变量名并传递给脚本
- 使用独立的cacheMap实例而非共享的KetherShell.mainCache，避免冲突
- 提供namespace列表，允许自定义脚本执行的命名空间

## 使用场景
> 在配置文件或消息文本中嵌入动态执行的Kether脚本
> 实现高级文本替换和格式化功能
> 在Language系统中支持动态内容生成
> 在不修改代码的情况下，通过配置文件定制复杂的文本处理逻辑

## 注意事项
> 只有当文本中包含"{{"标记时才会执行Kether解析，否则直接返回原文本
> 脚本执行结果会替换掉整个包含Kether表达式的文本部分
> args参数会被转换为arg0、arg1等变量名，在Kether脚本中可以直接引用
> 使用独立的缓存实例，与KetherShell.mainCache相互独立
