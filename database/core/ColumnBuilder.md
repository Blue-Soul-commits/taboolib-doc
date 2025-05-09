# ColumnBuilder

## 基本信息
- 类名和包路径: taboolib.module.database.ColumnBuilder
- 基本用途: 数据库列构建器的抽象基类
- 类型: 抽象类(Abstract Class)
- 所属模块: database

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> name: String? -> 列名

### 类方法
> name(name: String): Unit -> 设置列名
> getColumn(): Column -> 获取构建的列对象(抽象方法)

## 实现细节
- 作为SQL和SQLite列构建器的基类
- 提供基本的列名设置功能
- 定义抽象方法getColumn()由子类实现

## 子类

### SQL
> 用途: MySQL/MariaDB列构建器
> 字段:
> - type: ColumnTypeSQL? -> 列类型
> - extra: (ColumnSQL.() -> Unit)? -> 额外配置函数
> - parameter: Array<Int> -> 类型参数数组
> 方法:
> - type(type: ColumnTypeSQL, parameter1: Int, parameter2: Int, extra: ColumnSQL.() -> Unit): Unit -> 设置列类型和参数
> - extra(extra: ColumnSQL.() -> Unit): Unit -> 设置额外配置
> - id(): Unit -> 创建标准ID列(bigint unsigned not null auto_increment primary key)
> - timeCreate(): Unit -> 创建创建时间列(datetime not null default CURRENT_TIMESTAMP)
> - timeModified(): Unit -> 创建修改时间列(datetime not null default CURRENT_TIMESTAMP on update CURRENT_TIMESTAMP)
> - getColumn(): Column -> 构建并返回ColumnSQL对象

### SQLite
> 用途: SQLite列构建器
> 字段:
> - type: ColumnTypeSQLite? -> 列类型
> - extra: (ColumnSQLite.() -> Unit)? -> 额外配置函数
> - parameter: Array<Int> -> 类型参数数组
> 方法:
> - type(type: ColumnTypeSQLite, parameter1: Int, parameter2: Int, extra: ColumnSQLite.() -> Unit): Unit -> 设置列类型和参数
> - extra(func: ColumnSQLite.() -> Unit): Unit -> 设置额外配置
> - id(): Unit -> 创建标准ID列(integer not null primary key)
> - getColumn(): Column -> 构建并返回ColumnSQLite对象

## 使用场景
> 在Table类中通过add方法创建表列
> 在Host类中作为columnBuilder属性提供列构建功能
> 提供便捷方法创建常用列类型(如id、时间戳等)

## 注意事项
> SQL和SQLite子类提供了不同的列类型和选项支持
> 使用前必须设置列名和类型
> 预定义的常量方法(如id()、timeCreate())提供了标准列定义
