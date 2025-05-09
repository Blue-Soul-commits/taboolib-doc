# TypeSQLite

## 基本信息
- 类名和包路径: taboolib.expansion.TypeSQLite
- 基本用途: SQLite数据库的类型实现，用于定义基于文件的SQLite数据库连接和表结构
- 类型: 具体类，Type抽象类的实现
- 所属模块: database-player

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> file: File -> SQLite数据库文件
> tableName: String? -> 表名，如果为空则使用插件ID
> host: HostSQLite -> SQLite数据库主机配置
> tableVar: Table<*, *> -> 表示数据库表结构的Table对象

### 类方法
> host(): Host<*> -> 获取数据库主机配置
> tableVar(): Table<*, *> -> 获取数据库表配置

## 实现细节
- 继承自Type抽象类，实现了SQLite数据库的具体操作
- 在构造函数中接收数据库文件和可选的表名
- 使用newFile函数确保数据库文件存在，并通过getHost扩展函数创建HostSQLite对象
- 定义了标准的键值对存储表结构：
  - user字段：TEXT(64)，存储用户标识
  - key字段：TEXT(64)，存储键名
  - value字段：TEXT，存储值（无长度限制）
- 与TypeSQL不同，SQLite实现不使用自增ID字段

## 使用场景
> 单服务器环境下的玩家数据存储
> 不需要复杂数据库服务器的轻量级应用
> 作为Database类的底层实现，提供基于文件的数据存储
> 适用于插件的默认数据存储方式，无需额外配置

## 注意事项
> SQLite是基于文件的数据库，在高并发环境下性能可能不如专用数据库服务器
> 确保应用有足够的文件系统权限创建和访问数据库文件
> 适合中小规模数据存储，大规模数据可能需要考虑使用SQL数据库
