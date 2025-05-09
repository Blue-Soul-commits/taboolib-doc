# Lang
## 基本信息
- 类名和包路径: taboolib.module.lang.Lang
- 基本用途: 提供命令发送者的语言消息扩展函数，简化国际化消息的获取和发送
- 类型: Kotlin文件（包含扩展函数）
- 所属模块: minecraft-i18n

## 类结构
### 公开静态字段
> 无公开静态字段（文件中只包含扩展函数）

### 公开静态方法
> registerLanguage(vararg code: String): Unit -> 注册语言代码

### 类内可被访问字段
> 无类内字段（不是类，而是文件）

### 扩展函数
> ProxyCommandSender.sendLang(node: String, vararg args: Any): Unit -> 向命令发送者发送语言节点对应的消息
> ProxyCommandSender.asLangText(node: String, vararg args: Any): String -> 获取语言节点对应的文本，若节点不存在则返回"{$node}"
> ProxyCommandSender.asLangTextOrNull(node: String, vararg args: Any): String? -> 获取语言节点对应的文本，若节点不存在则返回null
> ProxyCommandSender.asLangTextList(node: String, vararg args: Any): List<String> -> 获取语言节点对应的文本列表
> ProxyCommandSender.getLocale(): String -> 获取命令发送者的语言设置
> ProxyCommandSender.getLocaleFile(): LanguageFile? -> 获取命令发送者对应的语言文件

## 实现细节
- Lang.kt提供了一系列扩展函数，简化了TabooLib国际化系统的使用
- sendLang方法根据命令发送者的语言设置发送对应的消息，如果节点不存在则发送"{$node}"
- asLangText方法获取语言节点对应的文本，如果节点不存在则返回"{$node}"
- asLangTextOrNull方法获取语言节点对应的文本，如果节点不存在则返回null
- asLangTextList方法获取语言节点对应的文本列表，支持TypeText和TypeList两种类型
- getLocale方法根据命令发送者类型获取语言设置，玩家使用Language.getLocale(player)，其他使用Language.getLocale()
- getLocaleFile方法获取命令发送者对应的语言文件，查找顺序为：
  1. 匹配命令发送者语言的文件(忽略大小写)
  2. 默认语言(Language.default)的文件
  3. 第一个可用的语言文件
- registerLanguage方法是Language.addLanguage的简化包装，用于注册新的语言代码

## 使用场景
> 在插件开发中，向玩家或控制台发送多语言消息
> 获取语言节点对应的文本，用于自定义处理或显示
> 获取语言节点对应的文本列表，用于多行消息或列表显示
> 获取命令发送者的语言设置，用于国际化处理
> 注册新的语言代码，扩展插件的语言支持

## 注意事项
> 所有方法都是ProxyCommandSender的扩展函数，只能在ProxyCommandSender实例上调用
> 如果语言文件不存在或节点不存在，sendLang方法会发送"{$node}"作为回退
> asLangText和asLangTextList方法在节点不存在时也会返回"{$node}"或包含该字符串的列表
> asLangTextOrNull方法在节点不存在时返回null，需要进行空检查
> getLocaleFile方法可能返回null，如果没有可用的语言文件
> 文本获取方法只支持TypeText和TypeList类型，其他类型会被视为不存在

