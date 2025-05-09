# Host
## 基本信息
- 类名和包路径: taboolib.module.database.Host
- 基本用途: 数据库连接地址的抽象基类，提供数据源创建和管理功能
- 类型: 抽象类
- 所属模块: database

## 类结构
### 公开静态字段
> dataSources: CopyOnWriteArrayList<HikariDataSource> -> 存储所有自动释放的数据源
> callbackClose: CopyOnWriteArrayList<Runnable> -> 存储数据库关闭时的回调函数

### 公开静态方法
> release(): Unit -> 释放所有数据源连接和执行回调函数

### 类内可被访问字段
> columnBuilder: ColumnBuilder -> 获取列构建器
> connectionUrl: String? -> 获取完整的数据库连接URL
> connectionUrlSimple: String? -> 获取简化的数据库连接URL
> driverClass: String -> 获取数据库驱动类名

### 类方法
> createDataSource(autoRelease: Boolean = true, withoutConfig: Boolean = false): DataSource -> 创建数据源

## 实现细节
- 使用泛型`<T : ColumnBuilder>`支持不同类型的列构建器
- 通过`Database`对象创建数据源，支持使用配置或不使用配置两种方式
- 使用`CopyOnWriteArrayList`线程安全集合存储数据源和回调函数
- 通过`@Awake(LifeCycle.DISABLE)`注解在插件禁用时自动释放资源

## 使用场景
> 作为各种数据库连接实现的基类，如HostSQL、HostSQLite、HostH2等
> 创建和管理数据库连接池
> 在应用程序关闭时自动释放数据库连接资源

## 注意事项
> 默认情况下创建的数据源会自动注册到`dataSources`中，在应用程序关闭时自动释放
> 可以通过`autoRelease = false`参数创建不自动释放的数据源，需要手动管理其生命周期
> 子类必须实现所有抽象属性
