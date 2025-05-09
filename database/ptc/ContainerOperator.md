# ContainerOperator

## 基本信息
- 类名和包路径: taboolib.expansion.ContainerOperator
- 基本用途: 提供数据库容器操作的抽象接口，定义了数据库表的基本操作方法
- 类型: 抽象类
- 所属模块: database-ptc

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> table: Table<*, *> -> 数据库表对象
> dataSource: DataSource -> 数据源对象，用于数据库连接

### 类方法
> keys(uniqueId: UUID): List<String> -> 获取指定UUID关联的所有键
> get(uniqueId: UUID): Map<String, Any?> -> 获取指定UUID关联的所有键值对
> get(uniqueId: UUID, vararg rows: String): Map<String, Any?> -> 获取指定UUID关联的特定行的键值对
> set(uniqueId: UUID, map: Map<String, Any?>): Unit -> 设置指定UUID关联的键值对
> select(filter: Filter.() -> Unit): Map<String, Any?> -> 根据过滤条件选择单条数据
> select(vararg rows: String, filter: Filter.() -> Unit): Map<String, Any?> -> 根据过滤条件选择特定行的单条数据
> selectAll(filter: Filter.() -> Unit): List<Map<String, Any?>> -> 根据过滤条件选择多条数据
> selectAll(vararg rows: String, filter: Filter.() -> Unit): List<Map<String, Any?>> -> 根据过滤条件选择特定行的多条数据
> update(map: Map<String, Any?>, filter: Filter.() -> Unit): Unit -> 根据过滤条件更新数据（仅限标准容器）
> insert(map: Map<String, Any?>): Unit -> 插入新数据（仅限标准容器）

## 实现细节
- 作为抽象类，定义了数据库容器操作的基本接口
- 提供了基于UUID的数据访问方法，适用于玩家数据管理
- 提供了基于过滤条件的数据查询、更新和插入方法
- 区分了标准容器特有的操作方法

## 使用场景
> 需要对数据库表进行基本CRUD操作的场景
> 需要管理玩家数据的插件
> 需要根据条件查询和操作数据的场景

## 注意事项
> 作为抽象类，需要具体实现类来提供实际功能
> update和insert方法仅限标准容器使用，其他类型容器可能不支持
> 实现类需要处理数据库连接和事务管理
> 操作大量数据时需要注意性能问题
