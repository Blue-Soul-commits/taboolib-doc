# Container
## 基本信息 
- 类名和包路径: taboolib.expansion.Container 
- 基本用途: 数据库容器抽象基类，管理数据表和数据库连接
- 类型: 抽象类
- 所属模块: module/database/database-ptc-object

## 类结构 
### 构造函数
> Container<T : ColumnBuilder>(val host: Host<T>) -> 接收数据库主机配置作为参数

### 公开字段 
> host: Host<T> -> 数据库主机配置
> map: ConcurrentHashMap<String, ContainerOperator> -> 存储表名与表操作器的映射关系
> dataSource: DataSource -> 数据库连接源

### 抽象方法
> protected abstract fun createTableObject(type: AnalyzedClass, name: String): Table<*, *> -> 创建表对象

### 公开方法
> open fun createTable(type: AnalyzedClass, name: String) -> 创建表并注册表操作器
> open fun init() -> 初始化所有表结构
> open fun path(): String -> 获取数据库连接路径
> open fun close() -> 关闭数据库连接
> open fun operator(name: String): ContainerOperator -> 获取指定名称的表操作器

## 实现细节
- Container是一个泛型类，泛型T必须是ColumnBuilder的子类
- 使用ConcurrentHashMap存储表名与操作器的映射，支持并发访问
- dataSource在构造时创建，设置autoRelease为false以手动管理资源释放
- createTable方法会创建表操作器并存储到map中
- init方法会遍历所有表并在数据库中创建对应表结构
- close方法用于释放数据库连接资源
- operator方法用于获取表操作器，若表不存在则抛出错误

## 使用场景 
> 作为数据库持久化框架的基础设施
> 管理多个数据表的创建、初始化和操作
> 在应用启动时初始化数据库结构
> 在应用关闭时释放数据库连接资源

## 注意事项 
> 使用前必须先调用createTable注册表结构
> 使用完毕后必须调用close方法释放资源
> 表名必须唯一，重复注册会覆盖之前的操作器
> 访问不存在的表会抛出异常