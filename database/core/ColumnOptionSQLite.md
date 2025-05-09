# ColumnOptionSQLite

## 基本信息
- 类名和包路径: taboolib.module.database.ColumnOptionSQLite
- 基本用途: 定义SQLite数据库列选项的枚举类
- 类型: 枚举类(Enum Class)
- 所属模块: database

## 类结构

### 公开静态字段
> NOTNULL: ColumnOptionSQLite -> 不能为空选项
> UNIQUE: ColumnOptionSQLite -> 唯一选项
> PRIMARY_KEY: ColumnOptionSQLite -> 主键选项
> AUTOINCREMENT: ColumnOptionSQLite -> 递增选项

### 公开静态方法
> 无

### 类内可被访问字段
> query: String -> 对应的SQLite语句片段

### 类方法
> 无

## 实现细节
- 每个枚举值都关联一个SQLite语句片段，用于生成列定义
- 枚举值代表了SQLite数据库中常用的列约束和属性
- 与ColumnOptionSQL相比，SQLite支持的选项较少，符合SQLite的简化设计理念

## 使用场景
> 在定义SQLite数据库表结构时指定列的约束条件
> 在ColumnSQLite类中用于生成列定义语句
> 在SQLite表创建DSL中用于设置列属性

## 注意事项
> 这些选项专用于SQLite数据库，不适用于MySQL/MariaDB等SQL数据库
> 在SQLite中，AUTOINCREMENT只能用于INTEGER PRIMARY KEY列
> SQLite的UNIQUE约束与SQL数据库的UNIQUE_KEY行为类似，但语法不同
