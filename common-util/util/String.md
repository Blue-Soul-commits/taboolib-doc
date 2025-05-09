# String

## 基本信息
- 类名和包路径: taboolib.common.util.String
- 基本用途: 提供字符串处理工具函数
- 类型: Kotlin扩展函数文件
- 所属模块: common-util

## 扩展函数
> String.replaceWithOrder(vararg args: Any): String -> 替换字符串中的变量占位符
> String.decodeUnicode(): String -> 解码字符串中的Unicode转义序列

## 实现细节
### replaceWithOrder
- 支持两种格式的占位符：
  - 数字索引占位符：`{0}`, `{1}`, `{2}`等
  - 命名占位符：`{name}`, `{id}`等
- 数字索引占位符按位置从args数组获取替换值
- 命名占位符需要在args中提供`Pair<Any, String>`类型参数，其中第二个值匹配占位符名称
- 如果找不到对应的替换值，保留原始占位符
- 使用StringBuilder优化字符串构建性能
- 通过字符级别的解析实现，而非使用正则表达式

### decodeUnicode
- 解析形如`\u0000`的Unicode转义序列
- 将十六进制Unicode编码转换为对应字符
- 使用StringBuilder优化字符串构建性能
- 通过字符级别的解析实现，处理每个转义序列

## 使用场景
> 需要格式化包含占位符的消息
> 处理包含Unicode转义序列的字符串
> 国际化和本地化文本处理
> 模板字符串替换

## 注意事项
> `replaceWithOrder`中数字索引从0开始
> 命名占位符需要使用Pair类型参数提供
> 如果找不到对应的替换值，原始占位符会保留在结果字符串中
> `decodeUnicode`只处理形如`\u0000`的标准Unicode转义序列
