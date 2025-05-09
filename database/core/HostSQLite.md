# HostSQLite
## 基本信息
- 类名和包路径: taboolib.module.database.HostSQLite
- 基本用途: SQLite数据库连接地址的实现类
- 类型: 数据类
- 所属模块: database

## 类结构
### 类内可被访问字段
> file: File -> SQLite数据库文件
> columnBuilder: ColumnBuilder -> 返回SQLite列构建器实例
> connectionUrl: String -> JDBC连接URL，指向SQLite文件
> connectionUrlSimple: String -> 简化的JDBC连接URL，与connectionUrl相同
> driverClass: String -> SQLite驱动类名，固定为"org.sqlite.JDBC"

### 类方法
> toString(): String -> 返回对象的字符串表示

## 实现细节
- 继承自`Host<SQLite>`类，专门用于SQLite数据库连接
- 使用Kotlin的data class特性，自动生成equals、hashCode等方法
- connectionUrl和connectionUrlSimple返回相同的值，因为SQLite不需要额外的连接参数
- 驱动类名固定为"org.sqlite.JDBC"

## 使用场景
> 创建基于文件的SQLite数据库连接
> 适用于轻量级、嵌入式数据库需求
> 单文件数据库，适合简单应用或本地存储

## 注意事项
> 确保SQLite驱动已正确加载
> 文件路径应该是有效的，且应用程序有权限读写该文件
> SQLite是基于文件的数据库，不支持多进程并发写入
