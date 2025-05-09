# Index

## 基本信息
- 类名和包路径: taboolib.module.database.Index
- 基本用途: 表示数据库表索引的数据类
- 类型: 数据类(Data Class)
- 所属模块: database

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> name: String -> 索引名称
> columns: List<String> -> 索引包含的列名列表
> unique: Boolean -> 是否为唯一索引，默认为false
> checkExists: Boolean -> 创建索引时是否检查索引是否已存在，默认为true

## 实现细节
- 使用Kotlin数据类简洁表示索引结构
- name和unique属性可变，支持后续修改
- columns属性不可变，确保索引列稳定性
- checkExists默认为true，避免重复创建索引错误

## 使用场景
> 在Table类中通过index方法创建表索引
> 在ExecutableSource中通过createIndex方法创建索引
> 在表创建时自动创建预定义的索引

## 注意事项
> 索引名称应遵循数据库命名规范
> 唯一索引(unique=true)会强制相关列的值唯一
> checkExists=true时会使用IF NOT EXISTS语法，兼容性更好
> 索引会影响INSERT/UPDATE性能，但提升SELECT性能