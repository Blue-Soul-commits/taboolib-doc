# SectionToSimpleComponent
## 基本信息
- 类名和包路径: taboolib.module.configuration.util.SectionToSimpleComponent
- 基本用途: 提供从配置节点获取聊天组件(SimpleComponent)的扩展函数
- 类型: 文件 (包含扩展函数)
- 所属模块: basic-configuration

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> ConfigurationSection.getComponent(node: String): SimpleComponent? -> 从配置节点获取聊天组件
> ConfigurationSection.getComponentToRaw(node: String): String? -> 从配置节点获取聊天组件并转换为原始JSON字符串

### 类内可被访问字段
> 无

### 类方法
> 无

## 实现细节
- 提供了 ConfigurationSection 的两个扩展函数，用于获取聊天组件
- 使用 taboolib.module.chat 模块的 component() 扩展函数将字符串转换为 SimpleComponent
- 使用 runCatching 安全地处理组件转换过程，避免因格式错误导致异常
- 在缺少聊天模块时，会抛出明确的错误信息，提示需要 "MinecraftChat" 模块
- getComponent 函数返回 SimpleComponent 对象，可用于发送富文本消息
- getComponentToRaw 函数返回组件的原始 JSON 字符串表示，通过调用 buildToRaw() 方法实现

## 使用场景
> 从配置文件中读取富文本消息
> 处理需要交互功能的聊天消息，如点击执行命令、显示提示文本等
> 创建具有复杂格式的游戏内通知
> 实现多语言支持的富文本界面元素

## 注意事项
> 这些函数依赖于 taboolib.module.chat 模块，使用前需确保该模块已加载
> 如果缺少聊天模块，函数会抛出错误而不是返回 null
> 配置中的文本需要符合 SimpleComponent 的语法要求
> 当配置节点不存在时，函数会返回 null

