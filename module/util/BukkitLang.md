# BukkitLang
## 基本信息
- 类名和包路径: taboolib.platform.util.BukkitLang
- 基本用途: 为Bukkit的CommandSender提供国际化语言支持的扩展函数
- 类型: Kotlin扩展函数集合
- 所属模块: bukkit-util

## 类结构
### 公开静态方法
> CommandSender.sendLang(node: String, vararg args: Any): Unit -> 向命令发送者发送语言节点对应的消息
> CommandSender.asLangTextOrNull(node: String, vararg args: Any): String? -> 获取语言节点对应的文本，若节点不存在则返回null
> CommandSender.asLangText(node: String, vararg args: Any): String -> 获取语言节点对应的文本，若节点不存在则返回"{$node}"
> CommandSender.asLangTextList(node: String, vararg args: Any): List<String> -> 获取语言节点对应的文本列表

## 实现细节
- 使用adaptCommandSender将Bukkit的CommandSender转换为跨平台的ProxyCommandSender
- 所有方法都是对taboolib.module.lang包中相应方法的封装
- 使用Kotlin的vararg关键字支持可变参数，并通过spread操作符(*)传递给底层方法
- 这些方法是对Bukkit平台的适配，使其能够使用TabooLib的国际化语言系统

## 使用场景
> 在Bukkit插件中实现多语言支持
> 向玩家或控制台发送本地化的消息
> 获取特定语言节点的文本，用于自定义消息处理
> 构建本地化的命令帮助信息或菜单

## 注意事项
> 使用前需要正确配置语言文件，通常放在plugins/插件名/lang/目录下
> 语言节点必须在语言文件中定义，否则asLangText会返回"{$node}"格式的占位符
> 参数替换使用有序替换，args参数会按顺序替换消息中的{0}、{1}等占位符
> 这些方法依赖于TabooLib的国际化模块，需要确保项目中引入了相关依赖

