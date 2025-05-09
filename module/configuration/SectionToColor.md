# SectionToColor
## 基本信息
- 类名和包路径: taboolib.module.configuration.util.SectionToColor
- 基本用途: 提供从配置节点获取带颜色代码的文本的扩展函数
- 类型: 文件 (包含扩展函数)
- 所属模块: basic-configuration

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> ConfigurationSection.getStringColored(node: String): String? -> 获取文本并应用颜色代码
> ConfigurationSection.getStringListColored(node: String): List<String> -> 获取文本列表并应用颜色代码

### 类内可被访问字段
> 无

### 类方法
> 无

## 实现细节
- 提供了 ConfigurationSection 的两个扩展函数，用于获取带颜色代码的文本
- 使用 taboolib.module.chat.colored 函数处理颜色代码转换
- 使用 runCatching 安全地处理颜色转换过程，避免因格式错误导致异常
- getStringColored 在节点不存在时返回 null，在颜色转换失败时也返回 null
- getStringListColored 在颜色转换失败时返回原始字符串列表，不会抛出异常

## 使用场景
> 从配置文件中读取带颜色代码的消息文本
> 处理游戏内聊天、标题、记分板等需要颜色的文本
> 读取带颜色格式的帮助信息或提示
> 加载多语言支持的彩色文本

## 注意事项
> 颜色代码转换依赖于 taboolib.module.chat 模块
> 如果颜色代码格式不正确，getStringColored 可能返回 null
> getStringListColored 在转换失败时会返回原始列表，而不是 null
> 这些函数只处理颜色代码，不会处理其他格式如粗体、斜体等
