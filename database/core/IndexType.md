# IndexType

## 基本信息
- 类名和包路径: taboolib.module.database.IndexType
- 基本用途: 定义数据库索引类型的枚举类
- 类型: 枚举类(Enum Class)
- 所属模块: database

## 类结构

### 公开静态字段
> BTREE: IndexType -> B+树索引
> HASH: IndexType -> 哈希索引
> DEFAULT: IndexType -> 默认索引

### 公开静态方法
> 无

### 类内可被访问字段
> 无

### 类方法
> 无

## 实现细节
- 定义了三种常见的数据库索引类型
- 不包含额外的属性或方法，仅作为类型标识

## 使用场景
> 在创建数据库索引时指定索引类型
> 在ColumnSQL类中用于设置列索引类型
> 在表创建DSL中用于定义索引结构

## 注意事项
> 不同数据库对索引类型的支持可能不同
> MySQL/MariaDB支持BTREE和HASH索引
> SQLite主要支持BTREE索引，不显式指定索引类型
> DEFAULT通常会使用数据库的默认索引类型，通常是BTREE
