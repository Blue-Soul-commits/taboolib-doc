# ActionFilterable

## 基本信息
- 类名和包路径: taboolib.module.database.ActionFilterable
- 基本用途: 提供支持过滤条件的数据库操作抽象基类
- 类型: 抽象类(Abstract Class)
- 所属模块: database

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> finallyCallback: (PreparedStatement.(Connection) -> Unit)? -> 操作执行完毕后的回调函数
> filter: Filter? -> 该行为的过滤器

### 类方法
> where(criteria: Criteria): Unit -> 追加一个过滤标准
> where(func: Filter.() -> Unit): Unit -> 函数式方式添加过滤条件
> append(criteria: Criteria): Unit -> 重写自Filterable的方法，空实现
> onFinally(onFinally: PreparedStatement.(Connection) -> Unit): Unit -> 设置操作完成后的回调
> callFinally(preparedStatement: PreparedStatement, connection: Connection): Unit -> 执行回调函数

## 实现细节
- 继承自Filterable，实现Action接口
- 提供两种添加过滤条件的方式：直接传入Criteria对象或使用DSL风格的函数式写法
- 管理操作完成后的回调函数，支持在SQL执行后处理结果

## 使用场景
> 作为ActionSelect、ActionUpdate、ActionDelete等具体操作类的基类
> 在数据库查询、更新、删除操作中添加WHERE条件
> 在操作完成后处理结果，如获取自增ID等

## 注意事项
> append方法是空实现，子类可能需要根据需要重写
> filter初始为null，首次调用where方法时会创建
> 可以多次调用where方法，条件会累加