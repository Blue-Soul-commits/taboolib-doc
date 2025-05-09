# 字符串工具扩展函数
## 基本信息
- 类名和包路径: taboolib.common5.util (Kotlin 扩展函数集)
- 基本用途: 提供增强的字符串操作功能和示例
- 类型: 扩展函数集和示例函数
- 所属模块: common5-legacy-api

## 类结构
### 公开静态方法
> String.startsWithAny(vararg prefix: String): Boolean -> 检查字符串是否以任一前缀开始
> String.endsWithAny(vararg suffix: String): Boolean -> 检查字符串是否以任一后缀结束
> String.substringAfterAny(vararg morePrefix: String): String -> 返回字符串中第一个匹配前缀之后的部分
> String.substringBeforeAny(vararg moreSuffix: String): String -> 返回字符串中第一个匹配后缀之前的部分
> String.replace(vararg pairs: Pair<String, Any>): String -> 批量替换字符串中的多个子串
> List<String>.replace(vararg pairs: Pair<String, Any>): List<String> -> 对字符串列表中的每个元素执行批量替换
> loreMapExample() -> LoreMap 使用示例函数

## 实现细节
- startsWithAny 和 endsWithAny 使用 Kotlin 的 any 函数检查是否有任何前缀/后缀匹配
- substringAfterAny 找到第一个匹配的前缀，然后返回其后的子串；如果没有匹配，则返回原字符串
- substringBeforeAny 找到第一个匹配的后缀，然后返回其前的子串；如果没有匹配，则返回原字符串
- replace 函数接受可变数量的键值对，依次执行替换操作
- List<String>.replace 扩展函数对列表中的每个字符串应用相同的替换规则
- loreMapExample 展示了 LoreMap 的基本用法，包括创建、添加规则和匹配

## 使用场景
> 需要检查字符串是否以多个可能的前缀或后缀开始/结束
> 需要提取字符串中特定前缀或后缀之前/之后的内容
> 需要在字符串中执行多次替换操作
> 处理游戏中的物品描述文本（lore）
> 配置文件解析和文本处理

## 注意事项
> substringAfterAny 和 substringBeforeAny 在没有匹配时返回原字符串，而不是空字符串
> replace 函数会将任何非字符串值转换为字符串后再替换
> LoreMap 示例展示了如何处理带有颜色代码的游戏文本

