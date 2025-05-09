# TextBlock
## 基本信息
- 类名和包路径: taboolib.module.chat.impl.TextBlock
- 基本用途: 表示聊天组件中的文本块，支持嵌套结构、属性设置和构建为ComponentText
- 类型: 类
- 所属模块: minecraft-chat

## 类结构
### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> level: Int -> 文本块的嵌套层级
> properties: MutableMap<String, PropertyValue?> -> 文本块的属性集合
> parent: TextBlock? -> 父文本块，可为null
> subBlocks: MutableList<TextBlock> -> 子文本块列表
> text: String -> 文本内容，通过builder获取

### 类方法
> plusAssign(char: Char): Unit -> 添加字符到文本内容
> createSubBlock(): TextBlock -> 创建子文本块并添加到subBlocks
> getSiblingBlocks(): List<TextBlock> -> 获取同级文本块
> toString(): String -> 打印文本块结构
> build(transfer: TextTransfer): ComponentText -> 构建为ComponentText对象

## 内部类
### NewLine
> 表示换行的特殊文本块，level为-1
> toString(): String -> 返回"NL"表示换行

## 实现细节
- TextBlock是DefaultSimpleComponent解析结果的核心数据结构，表示文本的层级结构
- 通过level属性表示嵌套层级，根文本块level为0，子文本块level递增
- 使用StringBuilder存储文本内容，通过plusAssign操作符(+=)添加字符
- properties存储文本块的属性，如颜色、点击事件、悬停文本等
- build方法是核心功能，将文本块转换为ComponentText对象
- build方法根据properties中的特殊属性决定文本类型(普通文本、按键、选择器、分数等)
- 支持多种属性设置，包括样式(粗体、斜体等)、交互(点击、悬停)和颜色
- 递归处理subBlocks，构建完整的组件树结构
- 提供了一个扩展的Map.get方法，支持通过多个key查找属性

## 使用场景
> 在DefaultSimpleComponent中，作为解析特殊格式文本的结果
> 表示聊天组件的层级结构，支持无限嵌套
> 存储和处理文本块的属性，如颜色、点击事件、悬停文本等
> 构建ComponentText对象，实现复杂的聊天组件效果

## 注意事项
> TextBlock通常不直接使用，而是由DefaultSimpleComponent创建和管理
> 属性处理中有多处错误检查，如缺少必要参数会抛出异常
> 颜色处理支持单字符颜色代码和RGB颜色值
> 悬停文本支持普通文本、多行文本(使用<br>或||分隔)和链接引用
> 翻译文本支持复杂的参数格式，包括有序参数和链接引用
