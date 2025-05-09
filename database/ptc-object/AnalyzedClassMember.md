# AnalyzedClassMember
## 基本信息 
- 类名和包路径: taboolib.expansion.AnalyzedClassMember 
- 基本用途: 解析和表示数据类成员属性，提供类型检查和注解信息访问
- 类型: 类
- 所属模块: module/database/database-ptc-object

## 类结构 
### 构造函数
> AnalyzedClassMember(private val root: Parameter, name: String, val isFinal: Boolean) -> 创建成员分析器，接收原始参数、名称和是否为final标记

### 属性
> val name: String -> 成员名称（数据库字段名称），会根据@Alias注解或命名规则转换
> val propertyName: String -> 原始属性名称
> val returnType: Class<*> -> 成员类型
> val isPrimary: Boolean -> 是否标记为@Id主键
> val isKey: Boolean -> 是否标记为@Key索引
> val isUniqueKey: Boolean -> 是否标记为@UniqueKey唯一索引
> val isNotNull: Boolean -> 是否标记为@NotNull非空
> val length: Int -> 字段长度，由@Length注解指定，默认为64
> val isFinal: Boolean -> 是否为不可变字段(val)
> val isBoolean: Boolean -> 是否为Boolean类型
> val isByte: Boolean -> 是否为Byte类型
> val isShort: Boolean -> 是否为Short类型
> val isByteArray: Boolean -> 是否为ByteArray类型
> val isInt: Boolean -> 是否为Int类型
> val isLong: Boolean -> 是否为Long类型
> val isFloat: Boolean -> 是否为Float类型
> val isDouble: Boolean -> 是否为Double类型
> val isChar: Boolean -> 是否为Char类型
> val isString: Boolean -> 是否为String类型
> val isUUID: Boolean -> 是否为UUID类型
> val isEnum: Boolean -> 是否为枚举类型
> val isCustomObject: Boolean -> 是否为自定义对象类型

### 方法
> fun canConvertedString(): Boolean -> 检查是否可以转换为字符串类型
> fun canConvertedNumber(): Boolean -> 检查是否可以转换为数字类型
> fun canConvertedInteger(): Boolean -> 检查是否可以转换为整数类型
> fun canConvertedDecimal(): Boolean -> 检查是否可以转换为小数类型
> override fun toString(): String -> 返回成员的字符串表示

### 伴生对象方法
> fun String.toColumnName(): String -> 将驼峰命名转换为下划线命名
> inline fun <reified T : Annotation> Parameter.findAnnotation(): T? -> 获取参数上的注解

## 实现细节
- 使用java.lang.reflect.Parameter作为根源数据
- 自动识别成员上的各种注解（@Id, @Key, @UniqueKey, @NotNull, @Length, @Alias）
- name属性优先使用@Alias注解指定的值，否则将属性名转换为下划线格式
- 提供全面的类型检查方法，支持基本类型、字符串、UUID、枚举和自定义对象
- 通过getAnnotationIfPresent获取参数上的注解，避免直接依赖可能不存在的注解
- 支持判断基本类型和包装类型（通过检查Class对象和基本类型对应的Class）
- canConverted系列方法提供类型转换能力，便于数据库映射

## 使用场景 
> 在ORM框架中分析数据类的成员属性
> 决定数据库表结构和列类型
> 处理数据类与数据库表之间的映射关系
> 支持数据序列化和反序列化过程

## 注意事项 
> name和propertyName可能不同，name用于数据库映射，propertyName用于Java对象访问
> isCustomObject判断较为简单，只是排除了所有已知的基本类型
> 字段名称转换遵循驼峰转下划线规则（如userName转为user_name）
> 类型判断同时考虑包装类和原始类型（如Boolean和boolean）
> final字段（val修饰）不能被更新操作修改

