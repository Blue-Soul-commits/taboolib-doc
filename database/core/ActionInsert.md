# ActionInsert

## 基本信息
- 类名和包路径: taboolib.module.database.ActionInsert
- 基本用途: 表示SQL INSERT操作的行为类
- 类型: 类(Class)
- 所属模块: database

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> table: String -> 要插入数据的表名
> keys: Array<String> -> 要插入的列名数组
> finallyCallback: (PreparedStatement.(Connection) -> Unit)? -> 操作完成后的回调
> values: ArrayList<Array<Any?>> -> 要插入的值列表
> duplicateUpdate: ArrayList<UpdateOperation> -> 重复键时的更新操作列表

### 类方法
> value(vararg args: Any?): Unit -> 添加一行插入值
> values(args: Array<Any?>): Unit -> 添加一行插入值(数组形式)
> values(args: List<Any?>): Unit -> 添加一行插入值(列表形式)
> onDuplicateKeyUpdate(func: DuplicateUpdateBehavior.() -> Unit): Unit -> 设置重复键时的更新行为
> onFinally(onFinally: PreparedStatement.(Connection) -> Unit): Unit -> 设置操作完成后的回调
> callFinally(preparedStatement: PreparedStatement, connection: Connection): Unit -> 执行回调函数

### 内部类
> DuplicateUpdateBehavior: 处理重复键更新的行为类
>   - updateOperations: ArrayList<UpdateOperation> -> 更新操作列表
>   - update(key: String, value: Any): Unit -> 添加更新操作

## 实现细节
- 实现Action接口，支持插入操作和重复键更新
- 通过Statement构建器生成INSERT SQL语句
- 支持多行数据插入
- 支持ON DUPLICATE KEY UPDATE语法处理重复键情况
- 提供多种添加值的方法，适应不同场景需求

## 使用场景
> 执行数据库插入操作
> 在ExecutableSource中通过insert方法创建和使用
> 在Table类中通过insert方法创建和使用
> 处理插入时的主键冲突情况

## 注意事项
> keys数组定义了要插入的列，values中的每个数组元素对应一行数据
> 每行数据的元素顺序必须与keys数组顺序一致
> onDuplicateKeyUpdate仅在MySQL/MariaDB中有效，其他数据库可能不支持
> 可以通过onFinally方法获取自增ID等操作结果