# LangQualify
## 基本信息
- 类名和包路径: taboolib.module.lang.LangQualify
- 基本用途: 提供命令发送者的语言消息扩展函数，支持不同级别的消息前缀和格式化
- 类型: Kotlin文件（包含扩展函数和枚举类）
- 所属模块: minecraft-i18n

## 类结构
### 公开静态字段
> 无公开静态字段（文件中只包含扩展函数和枚举类）

### 公开静态方法
> 无公开静态方法（文件中只包含扩展函数和枚举类）

### 类内可被访问字段
> 无类内字段（不是类，而是文件）

### 扩展函数
> ProxyCommandSender.sendInfo(node: String, vararg args: Any): Unit -> 发送INFO级别的语言节点消息
> ProxyCommandSender.sendWarn(node: String, vararg args: Any): Unit -> 发送WARN级别的语言节点消息
> ProxyCommandSender.sendError(node: String, vararg args: Any): Unit -> 发送ERROR级别的语言节点消息
> ProxyCommandSender.sendLang(level: Level, node: String, vararg args: Any): Unit -> 发送指定级别的语言节点消息
> ProxyCommandSender.sendInfoMessage(message: String, vararg args: Any): Unit -> 发送INFO级别的直接消息
> ProxyCommandSender.sendWarnMessage(message: String, vararg args: Any): Unit -> 发送WARN级别的直接消息
> ProxyCommandSender.sendErrorMessage(message: String, vararg args: Any): Unit -> 发送ERROR级别的直接消息
> ProxyCommandSender.sendMessage(level: Level, message: String, vararg args: Any): Unit -> 发送指定级别的直接消息
> ProxyCommandSender.asLangText(level: Level, node: String, vararg args: Any): String -> 获取带级别前缀的语言节点文本
> ProxyCommandSender.asLangTextList(level: Level, node: String, vararg args: Any): List<String> -> 获取带级别前缀的语言节点文本列表
> ProxyCommandSender.asQualifyText(level: Level, message: String, vararg args: Any): String -> 为消息添加级别前缀并格式化

### 枚举类
> Level -> 定义消息级别，包含INFO、WARN、ERROR三个级别

## 实现细节
- LangQualify提供了一系列扩展函数，用于发送带有级别前缀的消息
- 支持三种消息级别：INFO、WARN、ERROR，每种级别可以有不同的前缀
- 前缀查找逻辑：
  1. 首先尝试查找特定级别的前缀（如"prefix-info"）
  2. 如果找不到，尝试查找通用前缀"prefix"
  3. 如果仍找不到，使用默认前缀"§c[插件ID]"
- 提供了两种消息发送方式：
  - 通过语言节点发送（sendInfo、sendWarn、sendError、sendLang）
  - 直接发送消息文本（sendInfoMessage、sendWarnMessage、sendErrorMessage、sendMessage）
- 所有消息都会应用变量替换（replaceWithOrder）和颜色代码处理（colored）
- 提供了获取格式化文本的方法，可以在发送前进行自定义处理

## 使用场景
> 在插件开发中，提供统一的消息发送接口，支持不同级别的消息
> 实现带有插件前缀的消息系统，提高消息的可识别性
> 与TabooLib的国际化系统集成，支持多语言消息发送
> 在命令处理、事件监听等场景中，向玩家或控制台发送格式化消息
> 支持通过语言文件自定义消息前缀，提高插件的可配置性

## 注意事项
> 前缀查找依赖于asLangTextOrNull方法，该方法需要在ProxyCommandSender类中定义
> 消息格式化使用replaceWithOrder方法，支持%s格式和命名变量
> 颜色代码处理使用colored方法，支持&和§格式的颜色代码
> 默认前缀使用插件ID，通过pluginId函数获取
> 所有方法都是ProxyCommandSender的扩展函数，只能在ProxyCommandSender实例上调用
