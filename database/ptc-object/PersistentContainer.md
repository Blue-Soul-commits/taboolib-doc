# PersistentContainer
## 基本信息 
- 类名和包路径: taboolib.expansion.PersistentContainer 
- 基本用途: 持久化容器的便捷创建和管理工具，提供DSL风格API
- 类型: 类
- 所属模块: module/database/database-ptc

## 类结构 
### 属性
> val container: Container -> 内部持有的数据库容器实例

### 构造函数
> constructor(type: Any, flags: List<String> = emptyList(), clearFlags: Boolean = false, ssl: String? = null, builder: PersistentContainer.() -> Unit) -> 根据不同类型的数据源创建容器
> constructor(host: String, port: Int, user: String, password: String, database: String, flags: List<String> = emptyList(), clearFlags: Boolean = false, ssl: String? = null, builder: PersistentContainer.() -> Unit) -> 直接创建MySQL容器

### 方法
> fun container(name: String, server: Boolean = false, builder: ContainerBuilder.() -> Unit) -> 注册标准容器
> fun flatContainer(name: String, builder: ContainerBuilder.Flatten.() -> Unit = {}) -> 注册扁平容器
> operator fun get(name: String): ContainerOperator -> 获取表操作器
> fun close() -> 关闭容器并释放资源

### 顶层函数
> fun persistentContainer(type: Any, flags: List<String> = emptyList(), clearFlags: Boolean = false, ssl: String? = null, builder: PersistentContainer.() -> Unit): PersistentContainer -> 创建持久化容器（通用方式）
> fun persistentContainer(host: String = "localhost", port: Int = 3306, user: String = "root", password: String = "password", database: String = "minecraft", flags: List<String> = emptyList(), clearFlags: Boolean = false, ssl: String? = null, builder: PersistentContainer.() -> Unit): PersistentContainer -> 创建MySQL持久化容器

## 实现细节
- 提供DSL风格API，简化容器创建和表注册过程
- 支持多种数据源类型：
  - File对象 -> 创建SQLite容器
  - String路径 -> 创建SQLite容器（相对于插件数据文件夹）
  - ConfigurationSection -> 从配置读取MySQL连接信息
- 构造函数结束时自动调用container.init()初始化表结构
- container方法注册标准容器，支持server参数指定是否为服务器表
- flatContainer方法注册扁平容器，适用于键值对类型的数据
- get操作符重载提供对表操作器的简便访问
- close方法正确关闭底层数据库连接

## 使用场景 
> 插件快速创建和管理数据库连接
> 使用DSL风格API简化持久化配置
> 支持MySQL和SQLite数据库的统一接口
> 从配置文件读取数据库连接信息

## 注意事项 
> 使用完毕必须调用close()方法释放资源
> 对于SQLite，传入的File必须有效且父目录存在
> 对于ConfigurationSection，必须包含有效的host、port、user、password和database信息
> 使用扁平容器时，数据结构固定为键值对形式
> 在创建容器时应处理潜在的连接错误

