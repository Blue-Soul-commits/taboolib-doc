# BundleMap
## 基本信息 
- 类名和包路径: taboolib.expansion.BundleMap 
- 基本用途: 提供一个数据映射抽象接口，用于数据库对象-Kotlin数据类的反序列化过程
- 类型: 抽象类
- 所属模块: module/database/database-ptc-object

## 类结构 
### 抽象方法
> operator fun <T> get(name: String): T -> 获取指定名称的数据，使用泛型类型转换返回结果
> fun <T> getOrNull(name: String): T? -> 获取指定名称的数据，若不存在则返回null

## 实现细节
- BundleMap是一个抽象类，提供了两个抽象方法用于数据访问
- 默认实现为BundleMapImpl类，它接受一个Map<String, Any?>作为数据源
- 在AnalyzedClass中使用BundleMap作为数据反序列化的中间层
- 数据类可以通过在伴生对象中实现接收BundleMap参数的方法来自定义解析过程

## 使用场景 
> 作为数据库与Kotlin数据类之间的映射桥梁
> 在数据类的伴生对象中定义解包函数，从BundleMap中获取值构造对象
> 在TabooLib持久化框架中支持自定义数据类的反序列化过程

## 注意事项 
> get方法使用类型转换，如果类型不匹配会抛出ClassCastException
> 数据库字段名与数据类属性名的映射遵循驼峰转下划线规则（如serverName映射为server_name）
> 使用@Alias注解可以自定义字段映射名称，避免自动转换

