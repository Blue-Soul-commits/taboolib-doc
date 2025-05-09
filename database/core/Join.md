# Join

## 基本信息
- 类名和包路径: taboolib.module.database.Join
- 基本用途: 表示SQL JOIN操作的连接类
- 类型: 类(Class)
- 所属模块: database

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> joinType: JoinType -> 连接类型(LEFT, RIGHT, INNER)
> tableName: String -> 要连接的表名
> filter: Filter -> 连接条件过滤器

## 实现细节
- 实现Attributes接口，提供query属性生成JOIN SQL语句
- 支持三种连接类型：LEFT JOIN, RIGHT JOIN, INNER JOIN
- 使用Filter类定义ON条件
- 使用asFormattedColumnName()确保表名格式正确
- 重写elements属性提供SQL参数值列表

## 使用场景
> 在SQL查询中连接多个表
> 在ActionSelect类中通过innerJoin/leftJoin/rightJoin方法创建和使用
> 处理表间关系查询

## 注意事项
> 连接条件通过JoinFilter类的on方法设置
> 连接条件为空时不会生成ON子句
> 连接类型由JoinType枚举定义，目前支持LEFT/RIGHT/INNER三种类型
> 连接多个表时，连接顺序很重要，会影响查询结果