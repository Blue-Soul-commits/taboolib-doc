# JavaType

## 基本信息
- 类名和包路径: taboolib.common.util.JavType
- 基本用途: 提供Java原始类型和包装类型的工具
- 类型: Kotlin类型别名和扩展函数文件
- 所属模块: common-util

## 类型别名
> JavaByte = java.lang.Byte -> Java字节包装类
> JavaLong = java.lang.Long -> Java长整型包装类
> JavaDouble = java.lang.Double -> Java双精度浮点包装类
> JavaFloat = java.lang.Float -> Java单精度浮点包装类
> JavaShort = java.lang.Short -> Java短整型包装类
> JavaBoolean = java.lang.Boolean -> Java布尔包装类

## 属性
> JavaPrimitiveInt: Class<Int> -> Java int原始类型的Class对象
> JavaPrimitiveChar: Class<Char> -> Java char原始类型的Class对象
> JavaPrimitiveByte: Class<Byte> -> Java byte原始类型的Class对象
> JavaPrimitiveLong: Class<Long> -> Java long原始类型的Class对象
> JavaPrimitiveDouble: Class<Double> -> Java double原始类型的Class对象
> JavaPrimitiveFloat: Class<Float> -> Java float原始类型的Class对象
> JavaPrimitiveShort: Class<Short> -> Java short原始类型的Class对象
> JavaPrimitiveBoolean: Class<Boolean> -> Java boolean原始类型的Class对象

## 扩展函数
> Class<*>.nonPrimitive(): Class<*> -> 将原始类型转换为对应的包装类型

## 实现细节
- 使用`@file:Suppress("PLATFORM_CLASS_MAPPED_TO_KOTLIN")`抑制Kotlin将Java包装类映射到Kotlin类型的警告
- 使用`typealias`定义Java包装类的别名，便于在Kotlin代码中引用
- 使用属性获取器提供Java原始类型的Class对象
- `nonPrimitive()`函数使用when表达式将原始类型映射到对应的包装类型

## 使用场景
> 需要在Kotlin代码中明确引用Java包装类
> 需要获取Java原始类型的Class对象
> 需要在反射操作中将原始类型转换为包装类型
> 处理Java API需要包装类型而非原始类型的情况

## 注意事项
> Kotlin默认会将Java包装类映射到Kotlin基本类型，使用这些别名可以明确引用Java包装类
> 在大多数情况下，Kotlin会自动处理原始类型和包装类型之间的转换
> 这些工具主要用于反射和类型操作，而非普通的值操作
