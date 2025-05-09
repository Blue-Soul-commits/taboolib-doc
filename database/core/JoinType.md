# JoinType

## 基本信息
- 类名和包路径: taboolib.module.database.JoinType
- 基本用途: 定义SQL表连接类型的枚举类
- 类型: 枚举类(Enum Class)
- 所属模块: database

## 类结构

### 公开静态字段
> LEFT: JoinType -> 左连接
> RIGHT: JoinType -> 右连接
> INNER: JoinType -> 内连接

### 公开静态方法
> 无

### 类内可被访问字段
> 无

### 类方法
> 无

## 实现细节
- 定义了三种基本的SQL表连接类型
- 不包含额外的属性或方法，仅作为类型标识

## 使用场景
> 在SQL查询中指定表连接的类型
> 在Join类中用于构建连接语句
> 在ActionSelect类中用于定义表连接操作

## 注意事项
> 左连接(LEFT JOIN)会返回左表的所有行，即使右表中没有匹配的行
> 右连接(RIGHT JOIN)会返回右表的所有行，即使左表中没有匹配的行
> 内连接(INNER JOIN)只返回两表中都匹配的行
> 未包含外连接(FULL JOIN)，如需使用可能需要扩展此枚举