# PropertyValue
## 基本信息
- 类名和包路径: taboolib.module.chat.impl.PropertyValue
- 基本用途: 定义聊天组件属性值的接口，提供文本和链接两种属性值类型
- 类型: 接口
- 所属模块: minecraft-chat

## 类结构
### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> 无字段（接口本身没有字段）

### 类方法
> 无方法（接口本身没有方法）

## 内部类
### Text
> text: String -> 存储文本内容
> toString(): String -> 返回文本内容

### Link
> name: String -> 存储链接名称
> getValue(transfer: TextTransfer): ComponentText -> 获取链接对应的组件
> toString(): String -> 返回链接名称

## 实现细节
- PropertyValue是一个接口，定义了聊天组件属性值的基本行为
- 提供了两个内部实现类：Text和Link，分别表示文本类型和链接类型的属性值
- Text类简单存储文本内容，并通过toString方法返回该内容
- Link类存储链接名称，通过getValue方法从TextTransfer的组件中查找并构建对应的组件
- Link类的getValue方法使用非空断言(!!)获取链接数据，如果链接不存在会抛出异常
- 这两个类在DefaultSimpleComponent中用于解析和存储属性值

## 使用场景
> 在DefaultSimpleComponent中，用于存储解析出的属性值
> 在TextBlock中，用于处理文本块的属性
> 链接类型(Link)用于实现跨文本块的引用，支持复杂的组件结构
> 文本类型(Text)用于存储普通的属性文本值

## 注意事项
> Link类的getValue方法假设链接一定存在，如果链接不存在会抛出空指针异常
> 在使用Link类型前，应确保已经注册了对应名称的链接
> PropertyValue接口本身没有定义任何方法，仅作为Text和Link的共同类型标识
> 在DefaultSimpleComponent的解析过程中，属性值以@开头会被识别为Link类型

