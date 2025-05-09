# ActionSelect

## 基本信息
- 类名和包路径: taboolib.module.database.ActionSelect
- 基本用途: 表示SQL SELECT查询操作的行为类
- 类型: 类(Class)
- 所属模块: database

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> table: String -> 要查询的表名
> distincts: ArrayList<String> -> DISTINCT查询的列名列表
> rows: ArrayList<String> -> 要查询的列名列表，默认为["*"]
> join: ArrayList<Join> -> 表连接操作列表
> group: Group -> 分组操作
> order: ArrayList<Order> -> 排序操作列表
> sum: ArrayList<Sum> -> 求和操作列表
> limit: Int -> 结果数量限制，默认为-1(无限制)
> offset: Int -> 结果偏移量，默认为-1(无偏移)

### 类方法
> rows(vararg row: String): Unit -> 设置要查询的列
> distinct(vararg distinct: String): Unit -> 设置DISTINCT查询的列
> groupBy(vararg values: Any): Group -> 设置分组条件并返回Group对象
> order(row: String, desc: Boolean): Unit -> 设置排序(已废弃)
> orderBy(row: String, type: Order.Type, config: Order.() -> Unit): Unit -> 设置排序
> sum(row: String, tempRow: String, config: Sum.() -> Unit): Unit -> 添加求和操作
> limit(limit: Int): Unit -> 设置结果数量限制
> offset(offset: Int): Unit -> 设置结果偏移量
> innerJoin(table: String, func: JoinFilter.() -> Unit): Unit -> 添加内连接
> leftJoin(table: String, func: JoinFilter.() -> Unit): Unit -> 添加左连接
> rightJoin(table: String, func: JoinFilter.() -> Unit): Unit -> 添加右连接

### 继承方法(来自ActionFilterable)
> where(criteria: Criteria): Unit -> 添加过滤条件
> where(func: Filter.() -> Unit): Unit -> 函数式方式添加过滤条件
> onFinally(onFinally: PreparedStatement.(Connection) -> Unit): Unit -> 设置操作完成后的回调

## 实现细节
- 继承自ActionFilterable，支持WHERE条件过滤
- 通过Statement构建器生成SELECT SQL语句
- 支持多种SQL查询功能：列选择、DISTINCT、JOIN、GROUP BY、ORDER BY、LIMIT/OFFSET等
- rows和distincts互斥，设置一个会清空另一个
- 重写elements属性提供SQL参数值列表

## 使用场景
> 执行数据库查询操作
> 在ExecutableSource中通过select方法创建和使用
> 在Table类中通过select方法创建和使用
> 支持复杂的数据查询和分析需求

## 注意事项
> rows和distinct方法互斥，后调用的会覆盖先调用的设置
> 默认查询所有列(SELECT *)
> limit和offset为负数时不生成对应SQL子句
> 可以通过链式调用组合多种查询功能
