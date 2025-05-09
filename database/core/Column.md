# Column

## 基本信息
- 类名和包路径: taboolib.module.database.Column
- 基本用途: 数据库表列的抽象基类
- 类型: 抽象类(Abstract Class)
- 所属模块: database

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> query: String -> 生成的数据库列定义语句

### 类方法
> 无

## 实现细节
- 提供了一个抽象属性 `query`，用于生成数据库列的定义语句
- 作为 ColumnSQL 和 ColumnSQLite 等具体列类型的基类

## 使用场景
> 作为数据库表结构定义的基础组件
> 在创建表结构时用于定义列的类型、约束等

## 注意事项
> 子类必须实现 query 属性以提供具体的列定义语句
> 通常与 ColumnBuilder 配合使用来构建表结构
