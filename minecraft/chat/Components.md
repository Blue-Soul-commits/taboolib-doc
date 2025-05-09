# Components
## 基本信息
- 类名和包路径: taboolib.module.chat.Components
- 基本用途: 提供创建和解析各种聊天组件的工厂方法
- 类型: 单例对象(object)
- 所属模块: minecraft-chat

## 类结构
### 公开静态字段
> 无公开静态字段

### 公开静态方法
> empty(): ComponentText -> 创建空白的组件
> text(text: String): ComponentText -> 创建文本组件
> score(name: String, objective: String): ComponentText -> 创建分数文本组件
> keybind(key: String): ComponentText -> 创建按键文本组件
> selector(selector: String): ComponentText -> 创建选择器文本组件
> translation(text: String, vararg obj: Any): ComponentText -> 创建翻译文本组件
> translation(text: String, obj: List<Any>): ComponentText -> 创建翻译文本组件(列表参数版本)
> parseRaw(text: String): ComponentText -> 从原始JSON格式解析组件
> parseSimple(text: String): SimpleComponent -> 解析简化格式的文本
> parseSimpleToRaw(text: String, transfer: TextTransfer.() -> Unit): String -> 解析简化格式并转换为原始JSON
> parseSimpleToRaw(text: List<String>, transfer: TextTransfer.() -> Unit): List<String> -> 解析多个简化格式并转换为原始JSON列表
> parseSimpleToLegacyRaw(text: String, transfer: TextTransfer.() -> Unit): RawMessage -> 解析简化格式并转换为RawMessage
> parseSimpleToLegacyRaw(text: List<String>, transfer: TextTransfer.() -> Unit): List<RawMessage> -> 解析多个简化格式并转换为RawMessage列表

### 类内可被访问字段
> 无内部字段

### 类方法
> 无额外方法

## 实现细节
- Components是一个单例对象，提供了创建和解析各种聊天组件的工厂方法
- 使用@Inject注解标记为TabooLib注入对象
- 使用@RuntimeDependency注解声明运行时依赖，确保BungeeCord Chat API可用
- 所有创建组件的方法都返回DefaultComponent的实例，提供一致的接口
- parseSimple方法支持解析特殊的简化格式，格式为"文本1[特殊文本2](属性=属性值)文本3"
- 解析简化格式时使用try-catch处理异常，出错时返回ErrorSimpleComponent
- 提供多种转换方法，支持将简化格式转换为原始JSON或RawMessage

## 使用场景
> 作为TabooLib聊天模块的主要入口点，用于创建各种聊天组件
> 在需要构建复杂聊天消息的插件中使用
> 解析和处理特殊格式的文本，如带有属性的文本块
> 与其他聊天相关接口(ComponentText, SimpleComponent等)配合使用

## 注意事项
> 依赖BungeeCord Chat API，确保运行环境中有此依赖
> parseSimple方法解析的特殊格式需要遵循特定的语法规则
> 解析过程中可能出现异常，但会被捕获并返回ErrorSimpleComponent
> 转换方法(parseSimpleToRaw, parseSimpleToLegacyRaw)支持自定义文本转换

