# ComponentToString
## 基本信息
- 类名和包路径: taboolib.module.chat.ComponentToString
- 基本用途: 将Minecraft聊天组件(BaseComponent)转换为传统格式的带颜色代码的文本字符串
- 类型: 单例对象(object)
- 所属模块: minecraft-chat

## 类结构
### 公开静态字段
> 无公开静态字段

### 公开静态方法
> toLegacyString(vararg components: BaseComponent): String -> 将多个BaseComponent组件转换为传统格式的文本字符串

### 类内可被访问字段
> 无内部字段

### 类方法
> toLegacyString(component: BaseComponent): String -> 将单个BaseComponent组件转换为传统格式的文本字符串
> toLegacyString1(component: BaseComponent, builder: StringBuilder): String -> 递归处理组件及其子组件，将结果追加到StringBuilder中
> addFormat(component: BaseComponent, builder: StringBuilder): Unit -> 将组件的格式信息(颜色、粗体、斜体等)添加到StringBuilder中

## 实现细节
- ComponentToString是一个工具类，提供将现代聊天组件转换为传统格式文本的功能
- 公开的toLegacyString方法接受可变参数，可以处理多个BaseComponent组件
- 内部使用递归方式处理组件树结构，确保所有子组件都被正确转换
- 对于TranslatableComponent类型，由于逻辑复杂，使用反射调用其原始的toLegacyText方法
- 对于其他类型的组件(TextComponent, KeybindComponent, ScoreComponent, SelectorComponent)，分别提取其文本内容
- 在添加文本内容前，先处理组件的格式信息，包括颜色和各种文本样式(粗体、斜体、下划线、删除线、混淆)

## 使用场景
> 在需要将现代聊天组件转换为传统格式文本的场景中使用
> 在不支持或不需要使用JSON格式聊天组件的环境中，提供向下兼容的文本转换
> 在ComponentText接口的实现中，用于toLegacyText方法的实现
> 在需要提取聊天组件纯文本内容(带颜色代码)的场景中使用

## 注意事项
> 转换后的文本使用传统的颜色代码(§)，可能不支持现代聊天组件的所有特性
> 对于TranslatableComponent类型，使用反射调用原始方法，可能存在版本兼容性问题
> 转换过程会保留组件的颜色和样式信息，但会丢失交互功能(如点击事件、悬停事件等)
> 类注释中的类名为"ComponentToJson"，但实际类名为"ComponentToString"，可能是历史遗留问题