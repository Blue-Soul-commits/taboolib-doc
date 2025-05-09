# ContainerOperatorNormal

## 基本信息
- 类名和包路径: taboolib.expansion.ContainerOperatorNormal
- 基本用途: 实现标准数据容器的操作，提供行列结构的数据存储和访问
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
> player: Boolean -> 是否为玩家容器
> data: List<ContainerBuilder.Data> -> 数据列定义列表

### 类方法
> keys(uniqueId: UUID): List<String> -> 不支持，抛出错误
> get(uniqueId: UUID): Map<String, Any?> -> 获取指定UUID关联的所有列数据
> get(uniqueId: UUID, vararg rows: String): Map<String, Any?> -> 获取指定UUID关联的特定列数据
> set(uniqueId: UUID, map: Map<String, Any?>): Unit -> 设置指定UUID关联的列数据
> select(filter: Filter.() -> Unit): Map<String, Any?> -> 根据过滤条件选择单条数据
> select(vararg rows: String, filter: Filter.() -> Unit): Map<String, Any?> -> 根据过滤条件选择特定列的单条数据
> selectAll(filter: Filter.() -> Unit): List<Map<String, Any?>> -> 根据过滤条件选择多条数据
> selectAll(vararg rows: String, filter: Filter.() -> Unit): List<Map<String, Any?>> -> 根据过滤条件选择特定列的多条数据
> update(map: Map<String, Any?>, filter: Filter.() -> Unit): Unit -> 根据过滤条件更新数据，不存在则插入
> insert(map: Map<String, Any?>): Unit -> 插入新数据

## 实现细节
- 实现了ContainerOperator抽象类，提供标准容器的具体操作
- 标准容器使用行列结构，每行代表一个实体，每列代表一个属性
- 在set操作中，检查记录是否存在，存在则更新，不存在则插入
- 支持基于过滤条件的update和insert操作
- 所有操作都会过滤null值，确保数据完整性

## 使用场景
> 需要存储结构化数据的场景
> 适合存储实体数据，如玩家信息、游戏对象等
> 需要进行复杂查询和更新操作的场景

## 注意事项
> 不支持keys方法，调用会抛出错误
> 玩家容器(player=true)和非玩家容器的操作有所不同
> 非玩家容器不支持基于UUID的操作，调用会抛出错误
> 在update操作中，如果记录不存在会自动执行插入操作
> 查询返回的Map可能为空，需要进行空检查
