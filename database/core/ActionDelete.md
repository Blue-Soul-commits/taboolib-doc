# ActionDelete

## 基本信息
- 类名和包路径: taboolib.module.database.ActionDelete
- 基本用途: 表示SQL DELETE操作的行为类
- 类型: 类(Class)
- 所属模块: database

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> table: String -> 要删除数据的表名

### 类方法
> 无

### 继承方法(来自ActionFilterable)
> where(criteria: Criteria): Unit -> 添加过滤条件
> where(func: Filter.() -> Unit): Unit -> 函数式方式添加过滤条件
> onFinally(onFinally: PreparedStatement.(Connection) -> Unit): Unit -> 设置操作完成后的回调

## 实现细节
- 继承自ActionFilterable，支持WHERE条件过滤
- 重写query属性生成DELETE SQL语句
- 重写elements属性提供SQL参数值列表

## 使用场景
> 执行数据库删除操作
> 在ExecutableSource中通过delete方法创建和使用
> 在Table类中通过delete方法创建和使用

## 注意事项
> 不提供额外的功能方法，主要依赖ActionFilterable的where方法添加条件
> 没有添加WHERE条件时会删除表中所有数据，使用时需谨慎
> 可以通过onFinally方法添加操作完成后的回调处理