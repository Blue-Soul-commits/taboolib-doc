# Statement

## 基本信息
- 类名和包路径: taboolib.module.database.Statement
- 基本用途: SQL语句构建器，用于动态构建SQL查询语句
- 类型: 类(Class)
- 所属模块: database

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> query: ArrayList<String> -> 存储SQL语句片段的列表

### 类方法
> addSegment(literal: String): Statement -> 追加字符串语句片段
> addSegment(literal: List<String>): Statement -> 追加字符串列表语句片段
> addSegmentIfTrue(predicate: Boolean, builder: Statement.() -> Unit): Statement -> 条件性追加语句
> addSegmentSequence(prefix: String, suffix: String, builder: Statement.() -> Unit): Statement -> 追加带前后缀的语句序列
> addFilter(filter: Filter?): Statement -> 追加WHERE过滤条件
> addKeys(keys: Array<String>, useBrackets: Boolean, separator: CharSequence): Statement -> 追加列名
> addValue(values: Array<Any>): Statement -> 追加单行值占位符
> addValues(values: List<Array<Any?>>): Statement -> 追加多行值占位符
> addSpecialValue(value: Any): Statement -> 追加特殊值(非占位符)
> addOperations(operation: List<Attributes>, separator: CharSequence): Statement -> 追加操作列表
> build(): String -> 构建完整SQL语句

## 实现细节
- 使用流式API设计，每个方法都返回Statement自身，支持链式调用
- 内部使用ArrayList存储SQL片段，最终通过空格连接生成完整SQL
- 支持条件性添加语句片段，便于动态构建SQL
- 提供多种添加语句片段的方法，适应不同场景需求

## 使用场景
> 作为各种SQL操作(Select, Insert, Update, Delete)的基础构建器
> 在复杂查询中动态构建SQL语句
> 在各种Attributes实现类中生成特定SQL片段

## 注意事项
> 所有addSegment方法都返回this，支持链式调用
> addSegmentIfTrue和addSegmentSequence使用DSL风格的函数参数
> 使用asFormattedColumnName()确保列名格式正确
> build()方法使用空格连接所有片段，应确保片段间不需要额外空格

