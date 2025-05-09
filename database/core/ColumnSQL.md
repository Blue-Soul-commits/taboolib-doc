# ColumnSQL

## 基本信息
- 类名和包路径: taboolib.module.database.ColumnSQL
- 基本用途: 表示SQL数据库表中的列定义
- 类型: 类(Class)
- 所属模块: database

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> type: ColumnTypeSQL -> 列的SQL数据类型
> name: String -> 列名
> parameter: Array<Int> -> 类型参数数组，用于如tinyint(M)或decimal(N,M)
> options: Array<ColumnOptionSQL> -> 列选项数组，如NOT NULL、AUTO_INCREMENT等
> def: Any? -> 默认值
> onUpdate: String? -> ON UPDATE子句的值
> indexType: IndexType -> 索引类型
> desc: Boolean -> 是否为倒序索引

### 类方法
> parameter(parameter1: Int, parameter2: Int): Unit -> 设置类型参数
> options(vararg options: ColumnOptionSQL): Unit -> 设置列选项
> def(def: Any?): Unit -> 设置默认值
> onUpdate(onUpdate: String?): Unit -> 设置ON UPDATE子句
> indexType(indexType: IndexType): Unit -> 设置索引类型
> indexDesc(desc: Boolean): Unit -> 设置是否为倒序索引
> query: String -> 生成列定义SQL片段
> queryOptions: String -> 生成列选项SQL片段
> toString(): String -> 返回对象的字符串表示

### 继承方法(来自Column)
> query: String -> 生成列定义SQL片段(抽象属性，在本类中实现)

## 实现细节
- 继承自Column抽象类，实现query属性
- 使用Statement构建器生成SQL片段
- 支持类型参数、列选项、默认值、ON UPDATE子句等MySQL特性
- 特殊处理UNIQUE_KEY和KEY选项，它们不在queryOptions中生成，而是在表创建时单独处理
- 支持索引类型和倒序索引(MySQL 8.0+特性)

## 使用场景
> 定义MySQL/MariaDB表结构
> 在Table类中通过add方法创建和使用
> 在SQL类的getColumn方法中创建
> 通过ColumnTypeSQL的invoke操作符创建

## 注意事项
> parameter数组的第一个元素(index 0)表示主参数，第二个元素(index 1)表示次参数
> 默认值如果是字符串且包含单引号，需要使用转义符(\\')
> 非字符串的特殊类型默认值需要在前面添加$符号
> 倒序索引(desc=true)仅在MySQL 8.0及以上版本有效
