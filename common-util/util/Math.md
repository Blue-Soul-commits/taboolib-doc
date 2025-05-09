# NumberUtil

## 基本信息
- 类名和包路径: taboolib.common.util.NumberUtil
- 基本用途: 提供数字处理工具函数
- 类型: Kotlin扩展函数文件
- 所属模块: common-util

## 扩展函数
> Int.length(): Int -> 获取整数的位数
> Long.length(): Int -> 获取长整数的位数
> Int.digits(): List<Int> -> 获取整数的每一位数字列表
> Long.digits(): List<Int> -> 获取长整数的每一位数字列表

## 实现细节
### length函数
- `Int.length()`将整数转换为长整数后调用`Long.length()`
- `Long.length()`使用Guava的`LongMath.log10`计算数字的位数
- 对于0，特殊处理返回1
- 对于负数，使用`abs()`取绝对值后计算

### digits函数
- `Int.digits()`将整数转换为长整数后调用`Long.digits()`
- `Long.digits()`使用取模和除法提取每一位数字
- 对于0，特殊处理返回包含单个0的列表
- 对于负数，使用`abs()`取绝对值后计算
- 结果列表按从高位到低位的顺序排列(通过最后的`reverse()`)

## 使用场景
> 需要获取数字的位数
> 需要分解数字的每一位进行处理
> 数字格式化和显示
> 数学计算和算法实现

## 注意事项
> 对于非常大的数字，`length()`函数依赖于Guava的`LongMath.log10`实现
> 对于负数，这些函数处理的是其绝对值
> `digits()`函数返回的列表是从高位到低位排列的
> 对于0，`length()`返回1，`digits()`返回包含单个0的列表
