# ColumnOptionSQL

## 基本信息
- 类名和包路径: taboolib.module.database.ColumnOptionSQL
- 基本用途: 定义SQL数据库列选项的枚举类
- 类型: 枚举类(Enum Class)
- 所属模块: database

## 类结构

### 公开静态字段
> AUTO_INCREMENT: ColumnOptionSQL -> 递增选项
> ZEROFILL: ColumnOptionSQL -> 填充数字选项
> UNSIGNED: ColumnOptionSQL -> 无符号（非负数）选项
> NOTNULL: ColumnOptionSQL -> 非空选项
> PRIMARY_KEY: ColumnOptionSQL -> 主键选项
> UNIQUE_KEY: ColumnOptionSQL -> 唯一索引选项
> KEY: ColumnOptionSQL -> 普通索引选项

### 公开静态方法
> 无

### 类内可被访问字段
> query: String -> 对应的SQL语句片段

### 类方法
> 无

## 实现细节
- 每个枚举值都关联一个SQL语句片段，用于生成列定义
- 枚举值代表了SQL数据库中常用的列约束和属性

## 使用场景
> 在定义数据库表结构时指定列的约束条件
> 在ColumnSQL类中用于生成列定义语句
> 在表创建DSL中用于设置列属性

## 注意事项
> 这些选项专用于MySQL/MariaDB等SQL数据库，不适用于SQLite
> 某些选项组合可能有特定的顺序要求，如AUTO_INCREMENT通常与PRIMARY_KEY一起使用