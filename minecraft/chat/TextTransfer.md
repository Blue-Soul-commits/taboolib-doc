# TextTransfer
## 基本信息
- 类名和包路径: taboolib.module.chat.TextTransfer
- 基本用途: 提供文本转换功能，用于在构建聊天组件时对文本进行处理
- 类型: 类
- 所属模块: minecraft-chat

## 类结构
### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> component: DefaultSimpleComponent -> 关联的SimpleComponent组件，用于访问组件数据
> transforms: ArrayList<(String) -> String> -> 存储文本转换函数的列表

### 类方法
> invoke(text: Any?): String -> 内部操作符函数，应用所有转换器处理文本
> transform(block: (String) -> String): TextTransfer -> 添加自定义转换器
> colored(): TextTransfer -> 添加颜色转换器，对文本应用颜色代码
> uncolored(): TextTransfer -> 添加去色转换器，移除文本中的颜色代码

## 实现细节
- TextTransfer类作为文本转换器，主要用于SimpleComponent构建过程中的文本处理
- 构造函数接收一个DefaultSimpleComponent参数，建立与组件的关联
- 内部维护一个转换函数列表(transforms)，每个函数接收一个字符串并返回处理后的字符串
- 重载了invoke操作符，使实例可以像函数一样被调用，应用所有转换器处理文本
- transform方法允许添加自定义转换函数，实现灵活的文本处理
- colored和uncolored方法是预定义的转换器，分别用于应用颜色代码和移除颜色代码
- 所有方法都返回TextTransfer实例本身，支持链式调用

## 使用场景
> 在SimpleComponent的build方法中，用于对文本进行处理
> 在构建聊天组件时，实现文本的动态替换、格式化和颜色处理
> 与DefaultSimpleComponent配合，处理特殊格式文本中的变量和占位符
> 在国际化插件中，用于处理多语言文本的转换和格式化

## 注意事项
> TextTransfer实例通常由SimpleComponent的build方法创建和使用
> transforms列表中的转换函数会按添加顺序依次应用
> colored方法依赖于String.colored()扩展函数，确保该函数可用
> uncolored方法依赖于String.uncolored()扩展函数，确保该函数可用
> 自定义转换器应避免修改文本的结构，以免影响解析结果
