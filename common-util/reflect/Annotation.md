# AnnotatedElementExtensions
## 基本信息
- 类名和包路径: taboolib.common.reflect (Kotlin 扩展函数文件)
- 基本用途: 为 Java 反射 API 中的 AnnotatedElement 接口提供安全的注解操作扩展函数
- 类型: Kotlin 扩展函数文件
- 所属模块: common-reflect

## 类结构
### 公开静态方法
> getAnnotationIfPresent<T : Annotation>(annotationClass: Class<T>): T? -> 安全地获取指定类型的注解实例，如果不存在或获取过程中出现异常则返回 null
> hasAnnotation<T : Annotation>(annotationClass: Class<T>): Boolean -> 安全地判断元素是否存在指定类型的注解，避免可能出现的异常

## 实现细节
- 使用 try-catch 块包装原生的注解操作方法，防止在处理注解时可能出现的异常导致程序崩溃
- 特别处理了 `java.lang.ArrayStoreException: sun.reflect.annotation.AnnotationTypeMismatchExceptionProxy` 异常情况
- 作为扩展函数实现，可以直接在任何 AnnotatedElement 类型的对象上调用

## 使用场景
> 在需要安全获取类、方法、字段等元素上的注解时使用
> 在处理可能存在注解类型不匹配问题的代码中使用
> 在 TabooLib 的依赖注入和注解处理系统中使用

## 注意事项
> 这些扩展函数主要用于处理注解类型不匹配的情况，这通常发生在类加载器隔离或版本不兼容的环境中
> 与直接调用 AnnotatedElement 的方法相比，这些扩展函数会捕获所有异常并返回安全的默认值，可能会掩盖一些问题