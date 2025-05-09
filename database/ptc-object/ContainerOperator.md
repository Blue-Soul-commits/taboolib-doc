# ContainerOperator
## 基本信息 
- 类名和包路径: taboolib.expansion.ContainerOperator 
- 基本用途: 为对象持久化框架提供数据库表操作的抽象接口，支持对象-关系映射(ORM)
- 类型: 抽象类
- 所属模块: module/database/database-ptc-object

## 类结构 
### 抽象字段
> table: Table<*, *> -> 表对象
> dataSource: DataSource -> 数据源

### 泛型方法（内联扩展）
> inline fun <reified T> getOne(noinline filter: Filter.() -> Unit = {}): T? -> 获取符合条件的单个对象
> inline fun <reified T> get(noinline filter: Filter.() -> Unit = {}): List<T> -> 获取所有符合条件的对象
> inline fun <reified T> findOne(id: Any, noinline filter: Filter.() -> Unit = {}): T? -> 按ID查询单个对象
> inline fun <reified T> find(id: Any, noinline filter: Filter.() -> Unit = {}): List<T> -> 按ID查询多个对象
> inline fun <reified T> sort(row: String, limit: Int = 10, noinline filter: Filter.() -> Unit = {}): List<T> -> 正序排序对象
> inline fun <reified T> sortDescending(row: String, limit: Int = 10, noinline filter: Filter.() -> Unit = {}): List<T> -> 倒序排序对象
> inline fun <reified T> has(id: Any, noinline filter: Filter.() -> Unit = {}): Boolean -> 检查指定ID的对象是否存在
> inline fun <reified T> delete(id: Any, noinline filter: Filter.() -> Unit = {}) -> 删除指定ID的对象

### 抽象方法
> abstract fun <T> getOne(type: Class<T>, filter: Filter.() -> Unit = {}): T? -> 获取符合条件的单个对象
> abstract fun <T> get(type: Class<T>, filter: Filter.() -> Unit = {}): List<T> -> 获取所有符合条件的对象
> abstract fun <T> findOne(type: Class<T>, id: Any, filter: Filter.() -> Unit = {}): T? -> 按ID查询单个对象
> abstract fun <T> find(type: Class<T>, id: Any, filter: Filter.() -> Unit = {}): List<T> -> 按ID查询多个对象
> abstract fun <T> sort(type: Class<T>, row: String, limit: Int = 10, filter: Filter.() -> Unit = {}): List<T> -> 正序排序对象
> abstract fun <T> sortDescending(type: Class<T>, row: String, limit: Int = 10, filter: Filter.() -> Unit = {}): List<T> -> 倒序排序对象
> abstract fun update(data: Any, filter: Filter.() -> Unit = {}) -> 更新对象数据
> abstract fun updateByKey(data: Any) -> 按主键和索引键更新对象数据
> abstract fun insert(dataList: List<Any>) -> 插入对象数据
> abstract fun <T> has(type: Class<T>, id: Any, filter: Filter.() -> Unit = {}): Boolean -> 检查指定ID的对象是否存在
> abstract fun has(filter: Filter.() -> Unit): Boolean -> 检查符合条件的对象是否存在
> abstract fun <T> delete(type: Class<T>, id: Any, filter: Filter.() -> Unit = {}) -> 删除指定ID的对象

### 保护方法
> protected fun Any.value(): Any -> 将值转换为数据库可存储的格式

## 实现细节
- 提供两套API：内联泛型方法（适合Kotlin调用）和抽象方法（适合Java调用）
- 内联扩展方法通过reified类型参数提供类型安全的操作
- 使用Filter DSL构建查询条件
- 通过@Id注解标识数据类的主键
- 通过@Key注解标识数据类的索引键
- 支持UUID、基本类型和自定义类型的值转换
- updateByKey方法利用@Id和@Key定位数据，update方法仅使用@Id和自定义条件

## 使用场景 
> 对象关系映射(ORM)操作
> 数据库CRUD操作
> 复杂查询和条件过滤
> 数据排序和分页
> 对象持久化和反序列化

## 注意事项 
> 数据类必须有@Id注解标记的主键字段
> 使用update方法只会更新var修饰的可变字段
> 数据库字段名遵循驼峰转下划线规则
> 查询结果会通过BundleMap转换为对象
> 务必在容器不再使用时调用close()方法释放资源
