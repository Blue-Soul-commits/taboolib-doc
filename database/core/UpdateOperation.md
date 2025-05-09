# UpdateOperation

## 基本信息
- 类名和包路径: taboolib.module.database.UpdateOperation
- 基本用途: 表示SQL UPDATE操作中的单个字段更新
- 类型: 数据类(Data Class)
- 所属模块: database

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> query: String -> 更新语句片段(如: `name` = ?)
> value: Any? -> 更新的值，默认为null

## 实现细节
- 实现Attributes接口，提供query属性表示更新语句片段
- 使用data class简洁表示更新操作
- value属性可为null，支持将字段设为NULL值
- 不包含表名和WHERE条件，仅表示单个字段的更新操作

## 使用场景
> 在ActionUpdate类中通过set方法创建和使用
> 在ActionInsert类的onDuplicateKeyUpdate方法中使用
> 表示UPDATE语句中SET子句的单个部分

## 注意事项
> query通常是"`列名` = ?"格式，但也支持其他格式如"`列名` = `列名` + 1"
> 当使用预编译值时，query中包含?占位符，value提供实际值
> 当使用直接值(如数据库函数)时，query包含完整表达式，value为null
> 在ActionUpdate和DuplicateUpdateBehavior中自动创建，很少直接实例化
