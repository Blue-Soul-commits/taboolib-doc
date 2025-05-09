# BundleMapImpl
## 基本信息 
- 类名和包路径: taboolib.expansion.BundleMapImpl 
- 基本用途: 提供BundleMap的具体实现，通过包装Map实现数据库字段到Kotlin对象的映射转换
- 类型: 类（BundleMap的实现类）
- 所属模块: module/database/database-ptc-object

## 类结构 
### 构造函数
> BundleMapImpl(val map: Map<String, Any?>) -> 接收一个键值对映射作为数据源

### 公开字段
> map: Map<String, Any?> -> 存储实际的数据映射

### 类方法
> override fun <T> get(name: String): T -> 获取并转换指定名称的数据
> override fun <T> getOrNull(name: String): T? -> 安全获取指定名称的数据，若不存在则返回null

## 实现细节
- 通过内部持有的Map<String, Any?>实现数据存储
- get方法使用Kotlin的类型转换功能(as T)将存储的值转换为请求的类型
- getOrNull方法在调用get前先检查key是否存在，提供安全访问
- 使用@Suppress("UNCHECKED_CAST")注解来抑制无法避免的类型转换警告

## 使用场景 
> 在TabooLib持久化框架中包装数据库查询结果
> 在AnalyzedClass中用作数据反序列化媒介
> 在数据类的伴生对象中自定义解包函数时使用

## 注意事项 
> get方法使用强制类型转换，不兼容的类型会导致ClassCastException
> 不提供数据修改方法，仅用于数据读取
> 初始化后无法更改内部的数据映射
