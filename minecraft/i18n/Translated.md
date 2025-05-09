# Translated
## 基本信息
- 类名和包路径: taboolib.module.lang.inline.Translated
- 基本用途: 定义翻译对象的抽象基类，用于内嵌语言系统
- 类型: 抽象类
- 所属模块: minecraft-i18n

## 类结构
### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> node: String -> 翻译节点名称，用于在语言文件中查找对应的翻译
> default: T -> 默认值，当找不到翻译时使用

### 类方法
> get(locale: String = "zh_CN"): T -> 抽象方法，获取指定语言的翻译，默认为简体中文

## 实现细节
- Translated是一个泛型抽象类，T表示翻译内容的类型(如String或List<String>)
- 构造函数接收两个参数：node(翻译节点名称)和default(默认值)
- node字段用于在语言文件中查找对应的翻译
- default字段是可变的(var)，可以在运行时修改默认值
- get方法是抽象的，需要子类提供具体实现
- get方法默认参数为"zh_CN"，表示简体中文，可以根据需要指定其他语言代码

## 使用场景
> 作为内嵌语言系统的基础类，提供统一的翻译接口
> 在InlineLanguage中，用于创建TranslatedString和TranslatedStringList实例
> 在配置驱动的系统中，为配置项提供多语言支持
> 在插件开发中，简化国际化实现，减少代码重复
> 与TabooLib的国际化系统集成，提供一致的翻译机制

## 注意事项
> Translated是抽象类，不能直接实例化，需要使用其子类
> 默认语言为"zh_CN"(简体中文)，可以根据需要修改
> node字段通常通过配置文件注释中的@lang标记获取
> default字段是可变的，但通常不建议在初始化后修改
> 子类需要实现get方法，提供具体的翻译逻辑

