# TransArgument
## 基本信息
- 类名和包路径: taboolib.module.chat.impl.TransArgument
- 基本用途: 表示翻译文本组件中的参数，包含参数值和顺序信息
- 类型: 类
- 所属模块: minecraft-chat

## 类结构
### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> value: Any -> 参数值，可以是任意类型
> order: Int -> 参数顺序，用于确定参数在翻译文本中的位置

### 类方法
> 无额外方法

## 实现细节
- TransArgument是一个简单的数据类，用于存储翻译文本组件中的参数信息
- 包含两个主要属性：value(参数值)和order(参数顺序)
- value属性类型为Any，可以存储任意类型的参数值，包括字符串、数字、组件等
- order属性用于确定参数在翻译文本中的位置，便于按顺序排列参数
- 在TextBlock的build方法中，用于处理翻译文本的参数

## 使用场景
> 在TextBlock中，用于构建翻译文本组件(TranslatableComponent)的参数
> 处理特殊格式文本中的翻译文本属性，如arg0、arg1等
> 支持有序参数，确保参数按正确顺序应用到翻译文本中
> 与PropertyValue.Link配合，支持使用链接引用作为翻译参数

## 注意事项
> 在TextBlock中使用时，会根据order属性对参数进行排序
> 参数值(value)可以是任意类型，但在实际使用中通常是String或ComponentText
> 类名为TransArgument，但注释中显示为TranslationArgument，可能是历史遗留问题
