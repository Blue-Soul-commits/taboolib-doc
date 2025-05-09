# ResultProcessorList
## 基本信息
- 类名和包路径: taboolib.module.database.ResultProcessorList
- 基本用途: 管理和执行多个数据库结果处理器
- 类型: 开放类
- 所属模块: database

## 类结构
### 类内可被访问字段
> processors: MutableList<ResultProcessor> -> 存储多个结果处理器的列表
> source: ExecutableSource? -> 可选的可执行源，用于关闭连接
> isExecuted: Boolean -> 标记处理器列表是否已执行，只读属性

### 类方法
> run(): Int -> 执行所有处理器并返回最后一个处理器的结果
> find(): Boolean -> 执行所有处理器并返回最后一个处理器是否找到结果
> <T> first(resultSet: ResultSet.() -> T): T -> 执行所有处理器并返回最后一个处理器的第一个结果
> <T> firstOrNull(resultSet: ResultSet.() -> T): T? -> 执行所有处理器并返回最后一个处理器的第一个结果，如果没有结果则返回null
> <T> map(resultSet: ResultSet.() -> T): List<T> -> 执行所有处理器并返回最后一个处理器的所有结果列表
> forEach(resultSet: ResultSet.() -> Unit) -> 执行所有处理器并遍历最后一个处理器的所有结果
> forEachIndexed(resultSet: ResultSet.(index: Int) -> Unit) -> 执行所有处理器并带索引遍历最后一个处理器的所有结果

## 实现细节
- 构造函数接收处理器列表和可选的可执行源
- 初始化时检查处理器列表是否为空，为空则抛出错误
- 所有方法都会检查`isExecuted`标志，防止重复执行
- 执行时会先执行除最后一个处理器外的所有处理器，然后执行最后一个处理器并返回其结果
- 使用`try-finally`块确保无论执行成功与否都会关闭数据源连接

## 使用场景
> 在一个数据库连接中执行多个相关操作
> 在工作空间或事务中组合多个数据库操作
> 确保所有操作完成后自动关闭连接

## 注意事项
> 每个处理器列表只能执行一次，重复执行会抛出错误
> 最后一个处理器的结果会被返回，其他处理器的结果会被忽略
> 如果提供了`source`参数，执行完成后会自动关闭连接

