# Decoration
## 基本信息
- 类名和包路径: taboolib.module.chat.Decoration
- 基本用途: 定义文本装饰样式的枚举，用于聊天组件的样式设置
- 类型: 枚举类
- 所属模块: minecraft-chat

## 类结构
### 公开静态字段
> BOLD: Decoration -> 粗体文本样式
> ITALIC: Decoration -> 斜体文本样式
> UNDERLINE: Decoration -> 下划线文本样式
> STRIKETHROUGH: Decoration -> 删除线文本样式
> OBFUSCATED: Decoration -> 混淆(模糊)文本样式

### 公开静态方法
> values(): Array<Decoration> -> 返回包含所有枚举常量的数组
> valueOf(name: String): Decoration -> 返回指定名称的枚举常量

### 类内可被访问字段
> 无额外字段

### 类方法
> 无额外方法

## 实现细节
- Decoration枚举定义了Minecraft聊天系统中支持的五种文本装饰样式
- 每个枚举值对应一种特定的文本装饰效果
- 该枚举不包含颜色信息，仅表示文本的装饰样式
- 作为Kotlin枚举类，自动提供values()和valueOf(String)方法

## 使用场景
> 在ComponentText接口的实现中，用于设置文本的装饰样式
> 在聊天消息构建系统中，提供统一的文本样式定义
> 与其他聊天组件接口配合，实现丰富的文本格式化效果
> 在需要对文本应用多种样式的场景中使用

## 注意事项
> 不同的Minecraft版本对文本装饰的支持可能有所不同
> 在某些客户端或环境中，部分装饰效果可能不可见或显示异常
> OBFUSCATED(混淆)样式会使文本变为随机字符，通常用于特殊效果
> 装饰样式可以组合使用，例如同时应用粗体和斜体
