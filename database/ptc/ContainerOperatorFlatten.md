# ContainerOperatorFlatten

## 基本信息
- 类名和包路径: taboolib.expansion.ContainerOperatorFlatten
- 基本用途: 实现扁平化数据容器的操作，提供键值对形式的数据存储和访问
- 类型: 具体实现类
- 所属模块: database-ptc

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> table: Table<*, *> -> 数据库表对象
> dataSource: DataSource -> 数据源对象，用于数据库连接
> key: String -> 键列的名称
> value: String -> 值列的名称

### 类方法
> keys(uniqueId: UUID): List<String> -> 获取指定UUID关联的所有键
> get(uniqueId: UUID): Map<String, Any?> -> 获取指定UUID关联的所有键值对
> get(uniqueId: UUID, vararg rows: String): Map<String, Any?> -> 获取指定UUID关联的特定键的值
> set(uniqueId: UUID, map: Map<String, Any?>): Unit -> 设置指定UUID关联的键值对
> select(filter: Filter.() -> Unit): Map<String, Any?> -> 根据过滤条件选择单条数据
> select(vararg rows: String, filter: Filter.() -> Unit): Map<String, Any?> -> 根据过滤条件选择特定行的单条数据
> selectAll(filter: Filter.() -> Unit): List<Map<String, Any?>> -> 根据过滤条件选择多条数据
> selectAll(vararg rows: String, filter: Filter.() -> Unit): List<Map<String, Any?>> -> 根据过滤条件选择特定行的多条数据
> update(map: Map<String, Any?>, filter: Filter.() -> Unit): Unit -> 不支持，抛出错误
> insert(map: Map<String, Any?>): Unit -> 不支持，抛出错误

## 实现细节
- 实现了ContainerOperator抽象类，提供扁平化容器的具体操作
- 扁平化容器使用三列结构：username(用户标识)、key(键)和value(值)
- 在set操作中，区分已存在键(更新)和新键(插入)，分别执行不同的数据库操作
- 不支持直接的update和insert操作，这些操作在扁平化容器中没有意义
- 所有查询操作都基于键值对结构进行转换

## 使用场景
> 需要以键值对形式存储玩家数据的场景
> 适合存储配置、设置等简单结构的数据
> 需要频繁读写特定键值的场景

## 注意事项
> 不支持update和insert方法，调用这些方法会抛出错误
> 扁平化容器的表结构必须包含username、key和value三列
> 在set操作中，null值的键值对会被过滤，不会插入到数据库
> 查询返回的Map可能为空，需要进行空检查
