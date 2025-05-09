# TypeJson
## 基本信息
- 类名和包路径: taboolib.module.lang.TypeJson
- 基本用途: 实现Type接口，用于处理JSON格式的复杂消息，支持变量、颜色、交互等功能
- 类型: 类
- 所属模块: minecraft-i18n

## 类结构
### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> text: List<String>? -> 存储消息文本内容，可以是多行
> jsonArgs: ArrayList<Map<String, Any>> -> 存储消息的参数配置，如悬停文本、点击命令等

### 类方法
> init(source: Map<String, Any>): Unit -> 从配置源初始化消息内容和参数
> formated(string: String, sender: ProxyCommandSender, vararg args: Any): String -> 格式化字符串，应用翻译、变量替换和颜色处理
> send(sender: ProxyCommandSender, vararg args: Any): Unit -> 向指定接收者发送消息
> buildMessage(sender: ProxyCommandSender, vararg args: Any): ComponentText -> 构建完整的消息组件

## 实现细节
- TypeJson实现了Type接口，专门用于处理JSON格式的复杂消息
- 使用VariableReader解析文本中的变量，变量使用方括号([])包围
- init方法从配置中加载text和args，处理可能的类型转换异常
- formated方法对字符串应用三重处理：翻译、变量替换和颜色处理
- buildMessage是核心方法，负责构建完整的消息组件，包括处理变量、应用样式和添加交互功能
- 支持多种文本类型：普通文本、快捷键、选择器、翻译文本、分数和渐变色文本
- 支持多种交互功能：悬停文本、点击执行命令、建议命令、插入文本、复制到剪贴板、打开文件和URL
- 支持自定义字体设置

## 使用场景
> 在配置文件中定义复杂的交互式消息
> 创建带有悬停提示和点击功能的菜单或帮助信息
> 实现多语言支持的富文本消息系统
> 构建具有渐变色效果的视觉吸引力强的消息
> 在游戏内创建类似超链接的交互元素，如可点击的命令按钮

## 注意事项
> 配置格式需要遵循特定结构，text和args需要正确对应
> 变量使用方括号([])包围，每个变量需要在args中有对应的配置
> 如果变量数量与args不匹配，可能会显示错误信息"§c[RAW OPTION NOT FOUND]"
> 特殊文本类型(如translate、gradient)需要按照特定格式配置
> 在处理大量变量或复杂格式时，可能需要注意性能影响
