# TranslatedStringList
## 基本信息
- 类名和包路径: taboolib.module.lang.inline.TranslatedStringList
- 基本用途: Translated抽象类的实现，用于处理字符串列表类型的翻译
- 类型: 类
- 所属模块: minecraft-i18n

## 类结构
### 公开静态字段
> 无公开静态字段

### 公开静态方法
> of(value: List<String>): TranslatedStringList -> 创建一个固定值的TranslatedStringList实例，不进行实际翻译

### 类内可被访问字段
> 继承自Translated类:
> node: String -> 翻译节点名称
> default: List<String> -> 默认字符串列表值

### 类方法
> get(locale: String): List<String> -> 获取指定语言的翻译字符串列表

## 实现细节
- TranslatedStringList继承自Translated<List<String>>，专门用于处理字符串列表类型的翻译
- 构造函数接收两个参数：node(翻译节点名称)和default(默认字符串列表)
- get方法实现了从Language系统获取翻译的逻辑：
  1. 首先通过languageCodeTransfer映射转换语言代码
  2. 尝试按以下顺序查找语言文件：
     - 匹配指定语言代码的文件(忽略大小写)
     - 默认语言(Language.default)的文件
     - 任意可用的语言文件
  3. 如果找不到语言文件，返回默认值
  4. 根据节点类型进行不同处理：
     - 如果是TypeText类型，将文本转换为单元素列表
     - 如果是TypeList类型，过滤出TypeText类型的元素并提取文本
     - 其他类型，返回默认值
- companion object中的of方法提供了创建固定值TranslatedStringList的便捷方式，不进行实际翻译

## 使用场景
> 在内嵌语言系统中，用于处理字符串列表类型的翻译
> 通过InlineLanguage的getTranslatedStringList方法创建实例
> 在配置驱动的系统中，为列表类型的配置项提供多语言支持
> 在物品lore、命令帮助等多行文本场景中使用
> 与TabooLib的国际化系统集成，提供一致的翻译机制

## 注意事项
> get方法的查找逻辑依赖于Language系统的配置
> 语言代码匹配使用eqic方法，忽略大小写
> 如果找不到对应的翻译，会返回默认值
> 支持两种节点类型：TypeText(单行文本)和TypeList(文本列表)
> of方法创建的实例不会进行实际翻译，始终返回固定值
> 类设计为open，可以被继承和扩展
