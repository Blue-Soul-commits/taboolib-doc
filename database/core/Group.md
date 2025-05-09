# Group

## 基本信息
- 类名和包路径: taboolib.module.database.Group
- 基本用途: 表示SQL GROUP BY操作的分组类
- 类型: 类(Class)
- 所属模块: database

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> values: ArrayList<Any> -> 要分组的列或表达式列表
> rollup: Boolean -> 是否使用ROLLUP修饰符，默认为false

### 类方法
> reset(): Unit -> 重置分组设置，清空列表并关闭ROLLUP
> withRollup(): Unit -> 启用ROLLUP修饰符

## 实现细节
- 实现Attributes接口，提供query属性生成GROUP BY SQL语句
- 支持多列分组
- 支持WITH ROLLUP修饰符，用于生成分组的小计和总计
- 使用asFormattedColumnName()确保列名格式正确

## 使用场景
> 在SQL查询中指定分组方式
> 在ActionSelect类中用于添加GROUP BY子句
> 使用ROLLUP进行数据汇总分析

## 注意事项
> values列表可以包含列名或表达式
> ROLLUP修饰符会生成额外的汇总行
> 与HAVING子句配合使用可以过滤分组结果
> MySQL 8.0+支持更多分组选项如CUBE、GROUPING SETS等，可能需要扩展
