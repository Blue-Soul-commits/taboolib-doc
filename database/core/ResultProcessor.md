# ResultProcessor
## 基本信息
- 类名和包路径: taboolib.module.database.ResultProcessor
- 基本用途: 处理SQL查询结果的工具类
- 类型: 开放类
- 所属模块: database

## 类结构
### 公开静态字段
> Update: class -> 用于处理更新操作的内部类

### 类内可被访问字段
> query: String -> SQL查询语句
> executor: Executable<ResultSet> -> 结果集执行器
> isExecuted: Boolean -> 标记处理器是否已执行，只读属性

### 类方法
> run(): Int -> 运行查询并返回结果数量
> find(): Boolean -> 运行查询并返回是否有结果
> <T> first(call: ResultSet.() -> T): T -> 运行查询并返回第一个结果
> <T> firstOrNull(call: ResultSet.() -> T): T? -> 运行查询并返回第一个结果，如果没有结果则返回null
> <T> map(call: ResultSet.() -> T): List<T> -> 运行查询并返回所有结果的列表
> <T> mapNotNull(call: ResultSet.() -> T?): List<T> -> 运行查询并返回所有非空结果的列表
> forEach(call: ResultSet.() -> Unit) -> 运行查询并遍历所有结果
> forEachIndexed(call: ResultSet.(index: Int) -> Unit) -> 运行查询并带索引遍历所有结果

## 实现细节
- 使用`Executable<ResultSet>`接口执行SQL查询并处理结果
- 内部类`Update`专门用于处理更新操作，覆盖了`run()`方法
- 所有方法都会检查`isExecuted`标志，防止重复执行
- 使用Kotlin的扩展函数特性，允许在lambda表达式中直接访问ResultSet的方法
- 提供了两个已弃用的类型别名`QueryTask`和`QueryTasks`用于向下兼容

## 使用场景
> 执行SQL查询并处理结果集
> 执行更新、插入、删除等操作
> 在数据库操作中提取和转换数据

## 注意事项
> 每个处理器只能执行一次，重复执行会抛出错误
> 使用前应确保SQL查询语句正确
> 处理大量数据时应注意内存使用

