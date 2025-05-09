# Table
## 基本信息
- 类名和包路径: taboolib.module.database.Table
- 基本用途: 数据库表的抽象表示，提供表结构定义和数据操作功能
- 类型: 开放类
- 所属模块: database

## 类结构
### 类内可被访问字段
> name: String -> 表名
> host: Host<E> -> 数据库主机连接
> columns: ArrayList<Column> -> 表列定义集合
> primaryKeyForLegacy: ArrayList<String> -> 旧版主键定义集合
> indices: ArrayList<Index> -> 索引定义集合

### 类方法
> add(name: String? = null, func: E.() -> Unit): Table<T, E> -> 添加列定义
> index(name: String, columns: List<String>, unique: Boolean = false, checkExists: Boolean = true): Table<T, E> -> 添加索引定义
> createTable(dataSource: DataSource, checkExists: Boolean = true): Unit -> 创建表
> createIndex(dataSource: DataSource, name: String, columns: List<String>, unique: Boolean = false, checkExists: Boolean = true): Unit -> 创建索引
> select(dataSource: DataSource, func: ActionSelect.() -> Unit): ResultProcessorList -> 查询数据
> find(dataSource: DataSource, func: ActionSelect.() -> Unit): Boolean -> 查找数据是否存在
> update(dataSource: DataSource, func: ActionUpdate.() -> Unit): Int -> 更新数据
> delete(dataSource: DataSource, func: ActionDelete.() -> Unit): Int -> 删除数据
> insert(dataSource: DataSource, vararg keys: String, func: ActionInsert.() -> Unit): Int -> 插入数据（使用可变参数）
> insert(dataSource: DataSource, keys: List<String>, func: ActionInsert.() -> Unit): Int -> 插入数据（使用列表）
> workspace(dataSource: DataSource, func: ExecutableSource.() -> Unit): ResultProcessorList -> 创建工作空间
> transaction(dataSource: DataSource, func: ExecutableSource.() -> Unit): Result<Unit> -> 创建事务空间
> toString(): String -> 返回表的字符串表示

## 实现细节
- 使用泛型`<T : Host<E>, E : ColumnBuilder>`支持不同类型的数据库和列构建器
- 构造函数接收表名、主机连接和初始化函数，通过`func(this)`调用初始化函数
- 使用`@Suppress("LeakingThis")`注解抑制构造函数中泄露this的警告
- `add`方法使用`@Suppress("UNCHECKED_CAST")`进行类型转换
- 所有数据操作方法都通过`workspace`方法创建工作空间执行
- `transaction`方法创建事务空间，自动执行并提交事务

## 使用场景
> 定义数据库表结构
> 执行数据库CRUD操作
> 在单个连接中执行多个相关操作
> 使用事务确保数据一致性

## 注意事项
> 工作空间需要显式调用执行函数（如`run()`、`find()`等）才会执行操作
> 事务空间会自动执行并提交事务，不需要调用执行函数
> 工作空间中的`select`操作只会执行一次，且在`run()`之前
