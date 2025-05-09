# ColumnSQLite

## 基本信息
- 类名和包路径: taboolib.module.database.ColumnSQLite
- 基本用途: 表示SQLite数据库表中的列定义
- 类型: 类(Class)
- 所属模块: database

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> type: ColumnTypeSQLite -> 列的SQLite数据类型
> name: String -> 列名
> parameter: Array<Int> -> 类型参数数组，用于类型定义
> options: Array<ColumnOptionSQLite> -> 列选项数组，如NOT NULL、PRIMARY KEY等
> def: Any? -> 默认值

### 类方法
> parameter(parameter1: Int, parameter2: Int): Unit -> 设置类型参数
> options(vararg options: ColumnOptionSQLite): Unit -> 设置列选项
> def(def: Any?): Unit -> 设置默认值
> query: String -> 生成列定义SQL片段
> queryOptions: String -> 生成列选项SQL片段
> toString(): String -> 返回对象的字符串表示

### 继承方法(来自Column)
> query: String -> 生成列定义SQL片段(抽象属性，在本类中实现)

## 实现细节
- 继承自Column抽象类，实现query属性
- 使用Statement构建器生成SQL片段
- 支持类型参数、列选项、默认值等SQLite特性
- 相比ColumnSQL更简单，没有onUpdate、indexType和desc等MySQL特有功能

## 使用场景
> 定义SQLite表结构
> 在Table类中通过add方法创建和使用
> 在SQLite类的getColumn方法中创建
> 通过ColumnTypeSQLite的invoke操作符创建

## 注意事项
> parameter数组的第一个元素(index 0)表示主参数，第二个元素(index 1)表示次参数
> 默认值如果是字符串且包含单引号，需要使用转义符(\\')
> 非字符串的特殊类型默认值需要在前面添加$符号
> SQLite的类型系统比MySQL简单，大多数情况下参数不是必需的
