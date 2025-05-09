# ContainerSQL
## 基本信息 
- 类名和包路径: taboolib.expansion.ContainerSQL 
- 基本用途: MySQL/MariaDB数据库容器实现，提供SQL数据库的对象持久化支持
- 类型: 类（Container<SQL>的子类）
- 所属模块: module/database/database-ptc-object

## 类结构 
### 构造函数
> ContainerSQL(host: String, port: Int, user: String, password: String, database: String, flags: List<String> = emptyList(), clearFlags: Boolean = false, ssl: String? = null) -> 创建SQL数据库容器，配置连接参数

### 重写方法
> override fun createTableObject(type: AnalyzedClass, name: String): Table<*, *> -> 根据类的分析结果创建数据库表对象

### 私有方法
> private fun ColumnSQL.options(member: AnalyzedClassMember) -> 为列添加约束选项
> private fun AnalyzedClassMember.type(): ColumnTypeSQL -> 根据成员类型确定SQL列类型

## 实现细节
- 继承自Container<SQL>，专门用于MySQL/MariaDB数据库
- 构造函数接收数据库连接参数，并创建HostSQL实例
- 支持自定义连接标志（flags）和SSL配置
- createTableObject方法负责将Kotlin数据类映射为数据库表结构
- 自动为每个表添加id列
- 根据成员类型选择合适的数据库列类型：
  - 字符串和枚举类型 -> VARCHAR或LONGTEXT
  - UUID -> CHAR(36)
  - 字节数组 -> BLOB
  - 其他基本类型映射到对应的SQL类型
- 支持自定义类型通过CustomTypeFactory查找适合的处理器
- 通过注解自动设置列约束：
  - @Key或@Id -> 添加KEY约束
  - @UniqueKey -> 添加UNIQUE_KEY约束
  - @NotNull -> 添加NOTNULL约束
- 列长度通过@Length注解指定，默认为64

## 使用场景 
> 连接MySQL/MariaDB数据库进行对象持久化
> 将Kotlin数据类自动映射为数据库表
> 提供类型安全的数据库操作
> 支持自定义类型的序列化和反序列化

## 注意事项 
> 默认会为每个表添加id列，这是额外的，与@Id注解标记的主键不同
> 字符串类型默认使用VARCHAR，当@Length值小于0时使用LONGTEXT
> 不支持的类型会抛出"Unsupported type"异常
> 使用前需确保MySQL/MariaDB服务器可访问
> SSL参数会覆盖默认的useSSL=false设置
