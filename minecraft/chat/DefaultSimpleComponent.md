# DefaultSimpleComponent
## 基本信息
- 类名和包路径: taboolib.module.chat.impl.DefaultSimpleComponent
- 基本用途: 解析和构建特殊格式的文本组件，支持嵌套结构和属性设置
- 类型: 类
- 所属模块: minecraft-chat

## 类结构
### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> escapes: List<Char> -> 支持转义的字符列表，包括 [, ], (, ), ;, =, \
> root: ArrayList<TextBlock> -> 根文本块列表，存储解析后的文本结构
> links: ArrayList<String> -> 链接名称列表，用于引用其他文本块
> linkData: HashMap<String, DefaultSimpleComponent> -> 链接数据映射，存储链接引用的组件

### 类方法
> build(transfer: TextTransfer.() -> Unit): ComponentText -> 构建为ComponentText对象，并应用自定义转换
> build(transfer: TextTransfer): ComponentText -> 构建为ComponentText对象，应用指定的TextTransfer
> find(block: TextBlock, source: String, start: Int): Int -> 递归解析文本，构建文本块结构
> findToRight(source: String, char: Char, start: Int): Int -> 向右查找最近的指定字符
> split(delimiter: Char, source: String): List<String> -> 分割字符串并支持转义
> format(str: String): String -> 格式化字符串，处理转义字符

## 实现细节
- DefaultSimpleComponent实现了SimpleComponent接口，提供了解析和构建特殊格式文本的功能
- 支持解析的特殊格式为：文本1[特殊文本2](属性=属性值)文本3
- 初始化时会按行解析输入的文本，处理链接属性和构建文本块结构
- 使用递归方式解析嵌套的文本块，支持无限层级的嵌套
- 支持多种属性设置，如颜色、点击事件、悬停文本等
- 支持通过@链接名称引用其他文本块，实现复杂的组件结构
- 构建时会将文本块转换为ComponentText对象，并应用TextTransfer进行文本转换
- 优化了输出结构，避免出现多余的嵌套层级

## 使用场景
> 在需要使用简化语法创建复杂聊天组件的场景中使用
> 作为Components.parseSimple方法的核心实现，提供简化格式的解析功能
> 在配置文件中定义复杂的聊天消息，通过简单的语法实现丰富的效果
> 支持国际化插件中的消息格式化，结合TextTransfer实现文本转换

## 注意事项
> 特殊字符([, ], (, ), ;, =, \)需要使用反斜杠(\)进行转义
> 属性值中如果以@开头，会被视为链接引用，需要在文本中定义对应的链接
> 链接定义格式为"@链接名称=链接内容"，必须单独占一行
> 解析过程中如果遇到语法错误(如缺少右括号)，会抛出异常
> 构建时会自动移除最后一个空白文本块，优化输出结构
