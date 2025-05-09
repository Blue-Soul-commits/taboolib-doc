# IOCList

## 基本信息
- 类名和包路径: taboolib.expansion.ioc.linker.IOCList
- 基本用途: 提供类似ArrayList的接口连接IOC容器，但实际基于ConcurrentHashMap实现
- 类型: class
- 所属模块: database-ioc

## 类结构

### 类内可被访问字段
> ioc: ConcurrentHashMap<String, Any> -> 存储数据的实际容器，通过懒加载获取
> database: IOCDatabase -> 数据持久化接口，默认使用IOCDatabaseYaml

### 主要方法
> add(element: E): Boolean -> 添加元素到IOC容器
> remove(element: E): Boolean -> 从IOC容器中移除元素
> contains(element: E): Boolean -> 检查元素是否在IOC容器中
> get(index: String): Any? -> 通过索引ID获取元素
> set(index: String, element: Any): Any? -> 设置指定索引ID的元素
> forEachIOC(action: Pair<String, Any>.() -> Unit) -> 遍历IOC容器中的元素
> removeIfIOC(filter: Pair<String, Any>.() -> Boolean): Boolean -> 条件删除元素
> streamIOC(): Sequence<Map.Entry<String, Any>> -> 获取元素序列

## 实现细节
- 虽然继承自ArrayList，但实际上是基于ConcurrentHashMap实现
- 使用IndexReader.getIndexId获取对象的唯一索引ID
- 大多数基于索引位置的ArrayList方法被重写为抛出错误
- 提供了基于索引ID的替代方法
- 通过懒加载方式获取IOCReader中的数据映射

## 使用场景
> 需要List风格API但基于ID索引的数据管理
> 需要持久化存储的数据集合
> 需要线程安全的数据操作
> 作为IOC容器的数据链接器

## 注意事项
> 不支持基于位置索引的操作，如get(int)、set(int, E)等
> 使用索引ID而非对象引用进行对象标识
> 索引ID通过@Component注解的index属性或自动生成的UUID确定
> 大多数继承自ArrayList的方法被标记为@Deprecated或直接抛出错误