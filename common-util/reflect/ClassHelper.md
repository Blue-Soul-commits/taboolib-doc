# ClassHelper

## 基本信息
- 类名和包路径: taboolib.common.reflect.ClassHelper
- 基本用途: 提供类操作工具方法，无需使用反射
- 类型: 工具类(Utility Class)
- 所属模块: TabooLib 反射工具模块

## 类结构

### 公开静态字段
> PACKAGE_SEPARATOR_CHAR: char -> 包分隔符字符 '.'
> PACKAGE_SEPARATOR: String -> 包分隔符字符串 "."
> INNER_CLASS_SEPARATOR_CHAR: char -> 内部类分隔符字符 '$'
> INNER_CLASS_SEPARATOR: String -> 内部类分隔符字符串 "$"

### 公开静态方法
> getShortClassName(object: Object, valueIfNull: String): String -> 获取对象的短类名
> getShortClassName(cls: Class<?>): String -> 获取类的短类名
> getShortClassName(className: String): String -> 从字符串获取短类名
> getSimpleName(cls: Class<?>): String -> 获取类的简单名称
> getSimpleName(object: Object, valueIfNull: String): String -> 获取对象的简单名称
> getPackageName(object: Object, valueIfNull: String): String -> 获取对象的包名
> getPackageName(cls: Class<?>): String -> 获取类的包名
> getPackageName(className: String): String -> 从字符串获取包名
> getAbbreviatedName(cls: Class<?>, len: int): String -> 获取类的缩写名称
> getAbbreviatedName(className: String, len: int): String -> 从字符串获取缩写类名
> getAllSuperclasses(cls: Class<?>): List<Class<?>> -> 获取类的所有父类
> getAllInterfaces(cls: Class<?>): List<Class<?>> -> 获取类实现的所有接口
> convertClassNamesToClasses(classNames: List<String>): List<Class<?>> -> 将类名列表转换为类列表
> convertClassesToClassNames(classes: List<Class<?>>): List<String>> -> 将类列表转换为类名列表
> isAssignable(classArray: Class<?>[], toClassArray: Class<?>...): boolean -> 检查类数组是否可分配给另一个类数组
> isAssignable(classArray: Class<?>[], toClassArray: Class<?>[], autoboxing: boolean): boolean -> 带自动装箱选项的类数组分配检查
> isPrimitiveOrWrapper(type: Class<?>): boolean -> 检查类型是否为原始类型或包装类型
> isPrimitiveWrapper(type: Class<?>): boolean -> 检查类型是否为原始类型的包装类
> isAssignable(cls: Class<?>, toClass: Class<?>): boolean -> 检查一个类是否可分配给另一个类
> isAssignable(cls: Class<?>, toClass: Class<?>, autoboxing: boolean): boolean -> 带自动装箱选项的类分配检查
> primitiveToWrapper(cls: Class<?>): Class<?> -> 将原始类型转换为对应的包装类型
> primitivesToWrappers(classes: Class<?>...): Class<?>[] -> 将原始类型数组转换为包装类型数组
> wrapperToPrimitive(cls: Class<?>): Class<?> -> 将包装类型转换为对应的原始类型
> wrappersToPrimitives(classes: Class<?>...): Class<?>[] -> 将包装类型数组转换为原始类型数组
> isInnerClass(cls: Class<?>): boolean -> 检查类是否为内部类或静态嵌套类
> getClass(classLoader: ClassLoader, className: String, initialize: boolean): Class<?> -> 使用指定类加载器获取类
> getClass(classLoader: ClassLoader, className: String): Class<?> -> 使用指定类加载器获取并初始化类
> getClass(className: String): Class<?> -> 使用当前线程上下文类加载器获取并初始化类
> getClass(className: String, initialize: boolean): Class<?> -> 使用当前线程上下文类加载器获取类
> getPublicMethod(cls: Class<?>, methodName: String, parameterTypes: Class<?>...): Method -> 获取公共方法
> toClass(array: Object...): Class<?>[] -> 将对象数组转换为类数组
> getShortCanonicalName(object: Object, valueIfNull: String): String -> 获取对象的短规范名称
> getShortCanonicalName(cls: Class<?>): String -> 获取类的短规范名称
> getShortCanonicalName(canonicalName: String): String -> 从字符串获取短规范名称
> getPackageCanonicalName(object: Object, valueIfNull: String): String -> 获取对象的包规范名称
> getPackageCanonicalName(cls: Class<?>): String -> 获取类的包规范名称
> getPackageCanonicalName(canonicalName: String): String -> 从字符串获取包规范名称
> hierarchy(type: Class<?>): Iterable<Class<?>> -> 获取类层次结构的迭代器，不包括接口
> hierarchy(type: Class<?>, interfacesBehavior: Interfaces): Iterable<Class<?>> -> 获取类层次结构的迭代器，可选择是否包括接口

### 枚举类型
> Interfaces: 用于 hierarchy 方法的包含性字面量
  - INCLUDE: 包含接口
  - EXCLUDE: 排除接口

## 实现细节
- 基于 Apache Commons Lang3 的 ClassUtils 修改而来
- 使用静态映射表存储原始类型、包装类型和缩写之间的关系
- 修改了 Class.forName 的行为，使其指向 TabooLib.getClass
- 提供了丰富的类型转换和检查方法
- 支持处理数组类型和内部类
- 提供了类层次结构遍历功能

## 使用场景
> 获取类的简短名称或包名
> 检查类型兼容性和可分配性
> 在原始类型和包装类型之间转换
> 获取类的层次结构（父类和接口）
> 动态加载类
> 处理数组类型和内部类

## 注意事项
> 该类是从 Apache Commons Lang3 的 ClassUtils 修改而来，保留了大部分功能
> 类加载相关方法使用 TabooLib.getClass 而非标准的 Class.forName
> 大多数方法对 null 输入进行了安全处理
> 类型兼容性检查考虑了原始类型的宽化和自动装箱/拆箱
