# PersistentContainer

## 基本信息
- 类名和包路径: taboolib.expansion.PersistentContainer
- 基本用途: 提供持久化数据存储容器的实现，支持 SQLite 和 SQL 数据库
- 类型: 类
- 所属模块: database-ptc

## 类结构
### 公开静态方法
> persistentContainer(type: Any, flags: List<String> = emptyList(), clearFlags: Boolean = false, ssl: String? = null, builder: PersistentContainer.() -> Unit): PersistentContainer -> 创建持久化存储容器，支持文件类型或配置节类型
> persistentContainer(host: String = "localhost", port: Int = 3306, user: String = "root", password: String = "root", database: String = "minecraft", flags: List<String> = emptyList(), clearFlags: Boolean = false, ssl: String? = null, builder: PersistentContainer.() -> Unit): PersistentContainer -> 创建基于 SQL 的持久化存储容器

### 类内可被访问字段
> container: Container -> 存储容器实例

### 类方法
> container(name: String, server: Boolean = false, builder: ContainerBuilder.() -> Unit) -> 注册标准容器
> flatContainer(name: String, builder: ContainerBuilder.Flatten.() -> Unit = {}) -> 注册扁平容器
> get(name: String): ContainerOperator -> 获取容器操作器
> close() -> 关闭容器

## 实现细节
- 支持两种构造方式：基于文件/配置的构造和基于 SQL 参数的构造
- 自动识别数据源类型，支持 SQLite 和 SQL 数据库
- 提供标准容器和扁平容器两种数据存储模式
- 支持 SSL 连接和自定义连接标志

## 使用场景
> 需要持久化存储玩家数据的插件
> 需要管理服务器数据的应用
> 需要同时支持 SQLite 和 SQL 数据库的项目

## 注意事项
> 使用 SQLite 模式时，需要提供有效的文件对象或文件路径
> 使用 SQL 模式时，需要确保数据库连接参数正确
> 容器使用完毕后需要调用 close() 方法关闭连接

