# ContainerOperatorImpl
## 基本信息 
- 类名和包路径: taboolib.expansion.ContainerOperatorImpl 
- 基本用途: ContainerOperator抽象类的具体实现，提供对象与数据库之间的映射和操作功能
- 类型: 类（ContainerOperator的实现）
- 所属模块: module/database/database-ptc-object

## 类结构 
### 构造函数
> ContainerOperatorImpl(override val table: Table<*, *>, override val dataSource: DataSource) -> 接收表对象和数据源

### 类方法
> override fun <T> getOne(type: Class<T>, filter: Filter.() -> Unit): T? -> 获取符合条件的单个对象
> override fun <T> get(type: Class<T>, filter: Filter.() -> Unit): List<T> -> 获取所有符合条件的对象
> override fun <T> findOne(type: Class<T>, id: Any, filter: Filter.() -> Unit): T? -> 按ID查询单个对象
> override fun <T> find(type: Class<T>, id: Any, filter: Filter.() -> Unit): List<T> -> 按ID查询多个对象
> override fun <T> sort(type: Class<T>, row: String, limit: Int, filter: Filter.() -> Unit): List<T> -> 正序排序对象
> override fun <T> sortDescending(type: Class<T>, row: String, limit: Int, filter: Filter.() -> Unit): List<T> -> 倒序排序对象
> override fun update(data: Any, filter: Filter.() -> Unit) -> 更新对象数据
> override fun updateByKey(data: Any) -> 按主键和索引键更新对象数据
> override fun insert(dataList: List<Any>) -> 插入对象数据
> override fun <T> has(type: Class<T>, id: Any, filter: Filter.() -> Unit): Boolean -> 检查指定ID的对象是否存在
> override fun has(filter: Filter.() -> Unit): Boolean -> 检查符合条件的对象是否存在
> override fun <T> delete(type: Class<T>, id: Any, filter: Filter.() -> Unit) -> 删除指定ID的对象

## 实现细节
- 每个操作方法都首先通过AnalyzedClass.of()获取类型分析器，用于解析对象结构
- 所有查询操作通过SQL构造器创建查询条件，然后将结果映射回对象
- 使用table.select()方法执行查询，并通过typeClass.createInstance()将结果转换为对象
- update方法会先检查对象是否存在，存在则更新，不存在则插入
- updateByKey方法通过@Id和所有标记为@Key的字段进行条件过滤
- 更新操作只会更新非final的字段（在Kotlin中对应var修饰的属性）
- delete方法根据主键和过滤条件删除数据
- insert方法支持批量插入，提高性能

## 使用场景 
> 数据库对象持久化操作
> ORM框架的核心实现
> 提供类型安全的数据库操作接口
> 支持复杂查询、过滤和排序

## 注意事项 
> 数据类必须有@Id注解标记的主键字段，否则会抛出"No primary id found"异常
> 调用update方法时，数据类中必须存在可变字段（var修饰的属性），否则会抛出"No mutable field found"异常
> updateByKey方法需要至少一个标记为@Key的字段才能精确定位数据
> 字段名会按照命名约定转换（如serverName转为server_name）
> 在使用排序功能时，row参数应使用数据库字段名（通常是下划线形式）
