# HostSQL
## 基本信息
- 类名和包路径: taboolib.module.database.HostSQL
- 基本用途: MySQL/MariaDB数据库连接地址的实现类
- 类型: 具体类
- 所属模块: database

## 类结构
### 类内可被访问字段
> host: String -> 数据库主机地址
> port: String -> 数据库端口
> user: String -> 数据库用户名
> password: String -> 数据库密码
> database: String -> 数据库名称
> flags: ArrayList<String> -> 数据库连接参数列表
> flagsURL: String -> 格式化后的连接参数字符串
> columnBuilder: ColumnBuilder -> 返回SQL列构建器实例
> connectionUrl: String -> 完整的JDBC连接URL，包含连接参数
> connectionUrlSimple: String -> 简化的JDBC连接URL，不包含连接参数
> driverClass: String -> 数据库驱动类名

### 类方法
> constructor(section: ConfigurationSection) -> 从配置部分创建HostSQL实例
> toString(): String -> 返回对象的字符串表示

## 实现细节
- 继承自`Host<SQL>`类，专门用于MySQL/MariaDB数据库连接
- 默认包含三个连接参数：字符编码utf-8、禁用SSL、允许公钥检索
- 从配置文件中读取驱动类名，默认为"com.mysql.jdbc.Driver"
- 支持从ConfigurationSection直接构造，提供默认值

## 使用场景
> 创建MySQL/MariaDB数据库连接
> 与Table类结合使用进行数据库操作
> 在各种需要MySQL数据库连接的场景中使用

## 注意事项
> flags列表默认包含"allowPublicKeyRetrieval=true"，用于解决MySQL8版本的公钥检索问题
> 可以根据需要修改flags列表，添加或移除连接参数
> 驱动类名从settingsFile配置中读取，可以通过配置文件修改

