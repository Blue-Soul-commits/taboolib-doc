# Database
## 基本信息
- 类名和包路径: taboolib.module.database.Database
- 基本用途: 数据库连接池管理工具
- 类型: 单例对象
- 所属模块: database

## 类结构
### 类内可被访问字段
> settingsFile: Configuration -> 数据库配置文件，通过@Config注解自动加载

### 类方法
> prepareClose(func: Runnable): Unit -> 添加数据库关闭时的回调函数
> createDataSource(host: Host<*>, hikariConfig: HikariConfig? = null): DataSource -> 创建数据库连接池
> createDataSourceWithoutConfig(host: Host<*>): DataSource -> 不使用配置文件创建数据库连接池
> createHikariConfig(host: Host<*>): HikariConfig -> 创建HikariCP配置

## 实现细节
- 使用`@Inject`注解标记为注入类
- 使用`@RuntimeDependencies`注解声明运行时依赖
- 使用`@Config("datasource.yml")`注解自动加载配置文件
- 使用HikariCP作为连接池实现
- 支持从配置文件读取连接池参数
- 支持不同类型的数据库主机（如MySQL、SQLite等）

## 使用场景
> 创建和管理数据库连接池
> 配置数据库连接参数
> 为不同类型的数据库主机创建适合的连接池

## 注意事项
> 目前只支持HostSQL类型的用户名和密码设置，其他类型会抛出错误
> 配置文件中的参数会覆盖默认设置
> 运行时依赖使用了重定位技术，避免与其他插件的依赖冲突
