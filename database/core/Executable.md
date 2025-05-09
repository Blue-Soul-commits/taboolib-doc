# Executable

## 基本信息
- 类名和包路径: taboolib.module.database.Executable
- 基本用途: 提供数据库执行结果的回调函数接口
- 类型: 接口(Interface)
- 所属模块: database

## 类结构

### 公开静态字段
> Empty: Executable<ResultSet> -> 空回调实现，调用时抛出"Unsupported"错误

### 公开静态方法
> 无

### 类内可被访问字段
> 无

### 类方法
> invoke(func: T.() -> C): C -> 执行给定的函数并返回结果

## 实现细节
- 泛型接口，参数类型T通常为ResultSet或其他数据库结果类型
- 提供了一个Empty实现，用于表示不支持执行的情况
- invoke方法使用Kotlin的扩展函数语法，允许在T类型上下文中执行函数

## 使用场景
> 在数据库操作中处理查询结果
> 在ResultProcessor中用于处理SQL执行后的结果集
> 在ExecutableSource中用于执行查询和更新操作

## 注意事项
> Empty实现会在调用时抛出错误，应仅用于表示不支持的操作
> 实现类需要确保正确处理数据库资源，如关闭ResultSet