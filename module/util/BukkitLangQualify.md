# BukkitLangQualify
## 基本信息
- 类名和包路径: taboolib.platform.util.BukkitLangQualify
- 基本用途: 为Bukkit的CommandSender提供带有消息等级的国际化语言支持扩展函数
- 类型: Kotlin扩展函数集合
- 所属模块: bukkit-util

## 类结构
### 公开静态方法
> CommandSender.sendInfo(node: String, vararg args: Any): Unit -> 以INFO级别发送语言节点对应的消息
> CommandSender.sendWarn(node: String, vararg args: Any): Unit -> 以WARN级别发送语言节点对应的消息
> CommandSender.sendError(node: String, vararg args: Any): Unit -> 以ERROR级别发送语言节点对应的消息
> CommandSender.sendLang(level: Level, node: String, vararg args: Any): Unit -> 以指定级别发送语言节点对应的消息
> CommandSender.sendInfoMessage(message: String, vararg args: Any): Unit -> 以INFO级别发送直接消息
> CommandSender.sendWarnMessage(message: String, vararg args: Any): Unit -> 以WARN级别发送直接消息
> CommandSender.sendErrorMessage(message: String, vararg args: Any): Unit -> 以ERROR级别发送直接消息
> CommandSender.sendMessage(level: Level, message: String, vararg args: Any): Unit -> 以指定级别发送直接消息
> CommandSender.asLangText(level: Level, node: String, vararg args: Any): String -> 获取指定级别的语言节点对应的文本
> CommandSender.asLangTextList(level: Level, node: String, vararg args: Any): List<String> -> 获取指定级别的语言节点对应的文本列表

## 实现细节
- 使用adaptCommandSender将Bukkit的CommandSender转换为跨平台的ProxyCommandSender
- 所有方法都是对taboolib.module.lang包中相应方法的封装
- 支持三种消息级别：INFO、WARN和ERROR，每种级别可能有不同的前缀和颜色
- 提供了两类方法：基于语言节点的方法(sendLang系列)和直接消息的方法(sendMessage系列)
- 级别由taboolib.module.lang.Level枚举定义，用于控制消息的显示样式

## 使用场景
> 在Bukkit插件中实现带有不同重要性级别的多语言消息
> 发送带有统一前缀和格式的信息、警告和错误消息
> 构建具有一致视觉风格的用户界面消息
> 在不同情境下使用不同样式的消息，如成功操作、警告提示和错误通知

## 注意事项
> 使用前需要正确配置语言文件，通常放在plugins/插件名/lang/目录下
> 可以在语言文件中定义特定级别的前缀，如"prefix-info"、"prefix-warn"和"prefix-error"
> 如果未定义特定级别的前缀，将使用通用"prefix"，若都未定义则使用默认前缀"§c[插件ID]"
> 参数替换使用有序替换，args参数会按顺序替换消息中的{0}、{1}等占位符
