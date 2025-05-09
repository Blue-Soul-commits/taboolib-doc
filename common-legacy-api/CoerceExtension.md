# Coerce 扩展工具
## 基本信息
- 类名和包路径: taboolib.common5 (Kotlin 扩展属性和函数)
- 基本用途: 提供类型转换和格式化的便捷扩展
- 类型: 扩展属性和函数集
- 所属模块: common5-legacy-api

## 类结构
### 公开扩展属性
> Any?.cint: Int -> 将任意对象转换为整数
> Any?.cdouble: Double -> 将任意对象转换为双精度浮点数
> Any?.cfloat: Float -> 将任意对象转换为单精度浮点数
> Any?.clong: Long -> 将任意对象转换为长整数
> Any?.cshort: Short -> 将任意对象转换为短整数
> Any?.cbyte: Byte -> 将任意对象转换为字节
> Any?.cchar: Char -> 将任意对象转换为字符
> Any?.cbool: Boolean -> 将任意对象转换为布尔值
> Any?.cByteArray: ByteArray -> 将任意对象转换为字节数组

### 公开扩展函数
> Double.format(digits: Int = 2, roundingMode: Int = BigDecimal.ROUND_HALF_UP): Double -> 格式化双精度浮点数
> Float.format(digits: Int = 2, roundingMode: Int = BigDecimal.ROUND_HALF_UP): Float -> 格式化单精度浮点数
> String.eqic(other: String): Boolean -> 忽略大小写比较字符串

## 实现细节
- 所有类型转换扩展属性都使用 Coerce 类的相应方法实现
- 数值格式化函数使用 BigDecimal 进行精确的小数位控制
- 格式化函数包含异常处理，在出错时返回默认值 (0.0 或 0f)
- eqic 函数是 equals(other, ignoreCase = true) 的简写形式，提供更简洁的语法

## 使用场景
> 配置文件值的类型转换
> 用户输入的安全解析
> 数据库或网络返回值的类型转换
> 需要精确控制小数位数的数值显示
> 不区分大小写的字符串比较

## 注意事项
> 类型转换属性在无法转换时会返回默认值，而不是抛出异常
> 格式化函数在异常情况下会返回 0，可能导致静默错误
> 这些扩展依赖于 Coerce 类的实现，应查阅其文档了解具体的转换行为
