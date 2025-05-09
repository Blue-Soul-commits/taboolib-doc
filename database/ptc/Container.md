# Container

## 基本信息
- 类名和包路径: taboolib.expansion.Container
- 基本用途: 数据库容器的抽象基类，提供数据表管理和操作的基础功能
- 类型: 抽象类
- 所属模块: database-ptc

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> host: Host<*> -> 数据库主机对象，用于连接数据库
> hostTables: HashMap<String, Table<*, *>> -> 存储表名到表对象的映射
> hostTableOperator: HashMap<String, ContainerOperator> -> 存储表名到表操作器的映射
> dataSource: DataSource -> 数据源对象，通过unsafeLazy延迟初始化

### 类方法
> createTable(name: String, player: Boolean, playerKey: Boolean, data: List<ContainerBuilder.Data>): Table<*, *> -> 创建数据库表的抽象方法
> addTable(name: String, player: Boolean, playerKey: Boolean, data: List<ContainerBuilder.Data>): Unit -> 添加数据表并创建对应的操作器
> init(): Unit -> 初始化所有数据表
> path(): String -> 获取数据库连接URL
> close(): Unit -> 关闭数据源连接
> operator(name: String): ContainerOperator -> 获取指定表名的操作器

## 实现细节
- 作为抽象基类，定义了数据库容器的基本结构和行为
- 提供了表管理和操作器管理的通用实现
- 根据表的特性自动选择合适的操作器类型(扁平或标准)
- 使用unsafeLazy延迟初始化数据源，避免不必要的资源消耗
- 提供了资源管理方法(init和close)，确保正确初始化和释放资源

## 使用场景
> 作为数据库容器的基类，被具体数据库实现继承
> 管理多个数据表及其操作器
> 提供统一的数据库操作接口

## 注意事项
> 子类需要实现createTable抽象方法，提供特定数据库的表创建逻辑
> 使用完容器后应调用close方法释放资源
> 扁平容器的判断条件是：player=true, playerKey=false, data.size=2
> 文件顶部使用@file:Suppress("DEPRECATION")抑制了废弃警告，可能使用了一些已废弃的API