# Util
## 基本信息
- 类名和包路径: taboolib.module.chat.Util
- 基本用途: 提供聊天模块中的工具函数和扩展方法，包括颜色处理、文本转换等
- 类型: Kotlin文件（包含常量、扩展属性和扩展函数）
- 所属模块: minecraft-chat

## 类结构
### 公开静态字段
> EMPTY_TEXT: String -> 表示空文本的JSON字符串常量，值为"{\"text\":\"\"}"

### 公开静态方法
> 无公开静态方法（文件中只包含扩展函数和扩展属性）

### 类内可被访问字段
> 无类内字段（不是类，而是文件）

### 扩展属性和扩展函数
> Int.red: Int -> 获取整数颜色值的红色分量
> Int.green: Int -> 获取整数颜色值的绿色分量
> Int.blue: Int -> 获取整数颜色值的蓝色分量
> Int.mix(next: Int, d: Double): Int -> 将当前颜色与下一个颜色按比例混合
> String.component(): SimpleComponent -> 将字符串快速转换为SimpleComponent
> String.colored(): String -> 对字符串应用颜色代码
> String.uncolored(): String -> 移除字符串中的颜色代码
> List<String>.colored(): List<String> -> 对字符串列表中的每个元素应用颜色代码
> List<String>.uncolored(): List<String> -> 移除字符串列表中每个元素的颜色代码
> String.parseToHexColor(): Int -> 将字符串解析为整数颜色值
> String.toGradientColor(colors: List<Int>): String -> 创建渐变颜色文本
> List<Int>.gradientColor(position: Double): Int -> 根据位置计算渐变颜色

## 实现细节
- 提供了多种颜色处理工具，包括RGB分量提取、颜色混合和渐变色生成
- 支持多种颜色格式的解析，包括HEX(#FFFFFF)、RGB(255,255,255或255-255-255)和命名颜色
- 实现了字符串和字符串列表的颜色代码应用和移除
- 提供了创建渐变色文本的功能，可以将文本中的每个字符按照渐变色着色
- 实现了根据位置计算渐变色的功能，支持任意数量的颜色点
- 使用StandardColors枚举匹配命名颜色，支持英文和中文颜色名称

## 使用场景
> 在聊天消息中应用颜色代码，创建丰富多彩的文本
> 生成渐变色文本效果，增强视觉表现
> 解析各种格式的颜色表示，统一转换为整数颜色值
> 在UI设计中计算渐变色，实现平滑的颜色过渡
> 快速将字符串转换为SimpleComponent，便于构建复杂的聊天组件

## 注意事项
> parseToHexColor方法在无法解析颜色时会输出警告并返回0（黑色）
> toGradientColor方法要求colors列表至少包含两个颜色值
> gradientColor方法会将position参数限制在0.0到1.0之间
> 颜色混合和渐变计算使用线性插值，可能与感知上的颜色过渡有差异
> 使用命名颜色时，依赖StandardColors枚举的匹配功能

