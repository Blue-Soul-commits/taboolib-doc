# FileToHost
## 基本信息
- 包路径: taboolib.module.database
- 基本用途: 提供从文件或配置部分创建数据库主机连接的扩展函数
- 类型: Kotlin 扩展函数文件
- 所属模块: database

## 类结构
### 公开静态方法
> File.getHost(): HostSQLite -> 将文件对象转换为SQLite数据库主机连接
> ConfigurationSection.getHost(name: String): HostSQL -> 从配置部分获取SQL数据库主机连接

## 实现细节
- `File.getHost()` 扩展函数将文件对象直接传递给 `HostSQLite` 构造函数，用于创建SQLite数据库连接
- `ConfigurationSection.getHost(name: String)` 扩展函数从配置部分获取指定名称的子配置部分，并将其传递给 `HostSQL` 构造函数，用于创建SQL数据库连接
- 如果指定名称的配置部分不存在，则使用空配置

## 使用场景
> 快速从文件创建SQLite数据库连接
> 从配置文件中读取数据库连接信息并创建SQL数据库连接

## 注意事项
> `ConfigurationSection.getHost(name: String)` 方法在找不到指定名称的配置部分时会使用空配置，可能导致使用默认值创建数据库连接
> 使用前应确保文件路径有效或配置部分包含必要的数据库连接信息