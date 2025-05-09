# HostH2

## 基本信息
- 类名和包路径: taboolib.module.database.HostH2
- 基本用途: 提供H2数据库连接配置
- 类型: data class
- 所属模块: database-h2

## 类结构

### 类内可被访问字段
> file: File -> H2数据库文件

### 类方法
> columnBuilder: ColumnBuilder -> 获取SQL列构建器
> connectionUrl: String -> 获取完整的H2数据库连接URL
> connectionUrlSimple: String -> 获取简化的H2数据库连接URL
> driverClass: String -> 获取H2数据库驱动类名
> toString(): String -> 返回HostH2对象的字符串表示

## 实现细节
- 继承自Host<SQL>抽象类，实现了H2数据库的连接配置
- 使用MySQL兼容模式(MODE=MySQL)连接H2数据库
- 使用文件路径作为数据库位置

## 使用场景
> 需要使用H2数据库作为存储方式时
> 需要在本地文件系统中存储数据时
> 需要MySQL兼容模式的轻量级数据库时

## 注意事项
> H2数据库文件路径需要是有效的文件系统路径
> 使用前需要确保H2数据库驱动已正确加载
