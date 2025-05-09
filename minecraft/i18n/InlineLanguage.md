# InlineLanguage
## 基本信息
- 类名和包路径: taboolib.module.lang.inline.InlineLanguage
- 基本用途: 提供内嵌语言文件功能，通过配置文件注释定义翻译键
- 类型: Kotlin文件（包含扩展函数）
- 所属模块: minecraft-i18n

## 类结构
### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法（文件中只包含扩展函数）

### 类内可被访问字段
> 无类内字段（不是类，而是文件）

### 扩展函数
> ConfigurationSection.getTranslatedString(path: String): TranslatedString? -> 获取翻译字符串，如果路径不存在则返回null
> ConfigurationSection.getTranslatedString(path: String, def: String): TranslatedString -> 获取翻译字符串，如果路径不存在则使用默认值
> ConfigurationSection.getTranslatedStringList(path: String): TranslatedStringList -> 获取翻译字符串列表
> ConfigurationSection.getLanguageNode(path: String): String? -> 获取配置路径对应的语言节点名称

## 实现细节
- InlineLanguage提供了一种在配置文件中内嵌翻译键的机制，通过注释定义翻译键
- 使用特殊格式的注释`# @lang:翻译键`来标记配置项的翻译键
- getTranslatedString方法从配置中获取字符串，并检查是否有对应的翻译键
- getTranslatedString有两个重载版本，一个在路径不存在时返回null，另一个使用默认值
- getTranslatedStringList方法获取字符串列表，支持两种情况：
  - 配置项是列表类型，直接获取列表
  - 配置项是字符串类型，按行分割成列表
- getLanguageNode方法解析配置项的注释，查找以`@lang:`开头的注释行，提取翻译键
- 所有方法都支持颜色代码处理，使用getStringColored和getStringListColored

## 使用场景
> 在配置文件中定义多语言内容，无需单独的语言文件
> 为物品、技能、任务等游戏元素提供本地化支持
> 在插件开发中简化国际化实现，减少文件管理复杂度
> 与TabooLib的国际化系统集成，提供统一的翻译机制
> 在配置驱动的系统中，为配置项添加翻译支持

## 注意事项
> 翻译键必须在配置项的注释中定义，格式为`# @lang:翻译键`
> 配置文件必须支持注释读取，否则无法获取翻译键
> 如果没有找到翻译键，会返回原始值或默认值
> TranslatedString和TranslatedStringList类需要单独了解其用法
> 颜色代码处理依赖于taboolib.module.configuration.util模块
