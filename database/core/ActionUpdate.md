# ActionUpdate

## 基本信息
- 类名和包路径: taboolib.module.database.ActionUpdate
- 基本用途: 表示SQL UPDATE更新操作的行为类
- 类型: 类(Class)
- 所属模块: database

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> table: String -> 要更新的表名
> operations: ArrayList<UpdateOperation> -> 更新操作列表

### 类方法
> set(key: String, value: Any?): Unit -> 设置要更新的字段和值

### 继承方法(来自ActionFilterable)
> where(criteria: Criteria): Unit -> 添加过滤条件
> where(func: Filter.() -> Unit): Unit -> 函数式方式添加过滤条件
> onFinally(onFinally: PreparedStatement.(Connection) -> Unit): Unit -> 设置操作完成后的回调

## 实现细节
- 继承自ActionFilterable，支持WHERE条件过滤
- 通过Statement构建器生成UPDATE SQL语句
- 使用UpdateOperation类表示每个字段的更新操作
- 支持三种更新方式：设为NULL、设为预定义值(PreValue)、设为参数值
- 重写elements属性提供SQL参数值列表

## 使用场景
> 执行数据库更新操作
> 在ExecutableSource中通过update方法创建和使用
> 在Table类中通过update方法创建和使用
> 在ContainerOperator中用于更新对象数据

## 注意事项
> 没有设置任何字段(operations为空)时会生成无效的UPDATE语句
> 没有设置WHERE条件时会更新表中所有行，可能导致意外结果
> 支持将字段设为NULL值
> 支持使用PreValue设置数据库函数或表达式
