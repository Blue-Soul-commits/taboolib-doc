# ContainerSQLite
## 基本信息 
- 类名和包路径: taboolib.expansion.ContainerSQLite 
- 基本用途: SQLite数据库容器实现，提供轻量级文件数据库的对象持久化支持
- 类型: 类（Container<SQLite>的子类）
- 所属模块: module/database/database-ptc-object

## 类结构 
### 构造函数
> ContainerSQLite(file: File) -> 创建SQLite数据库容器，指定数据库文件

### 重写方法
> override fun createTableObject(type: AnalyzedClass, name: String): Table<*, *> -> 根据类的分析结果创建数据库表对象

### 私有方法
> private fun ColumnSQLite.options(member: AnalyzedClassMember) -> 为列添加约束选项

## 实现细节
- 继承自Container<SQLite>，专门用于SQLite文件数据库
- 构造函数接收一个File对象作为数据库文件
- createTableObject方法负责将Kotlin数据类映射为SQLite表结构
- 根据成员类型选择合适的SQLite列类型：
  - 字符串和枚举类型 -> TEXT
  - UUID -> TEXT(36)
  - 整数类型（Boolean、Byte、Short、Int、Long、Char）-> INTEGER
  - 小数类型（Float、Double）-> REAL
  - 字节数组 -> BLOB
  - 其他类型通过CustomTypeFactory查找处理器，无法处理则抛出异常
- 通过注解自动设置列约束：
  - @Id -> 添加PRIMARY_KEY约束
  - @UniqueKey -> 添加UNIQUE约束
  - @NotNull -> 添加NOTNULL约束
- 与ContainerSQL不同，SQLite版本不会自动添加额外的id列

## 使用场景 
> 需要轻量级文件数据库时使用SQLite进行对象持久化
> 单机应用或小型应用的数据存储
> 将Kotlin数据类自动映射为SQLite表
> 不需要完整SQL服务器的场景

## 注意事项 
> SQLite对复杂查询和并发操作的支持有限
> 表主键需要使用@Id注解标记，不会自动添加额外的id列
> 不支持的自定义类型必须通过CustomTypeFactory注册，否则会抛出异常
> 不同于MySQL，@Key注解在SQLite中没有直接效果，只有@Id才会设置为PRIMARY_KEY
> SQLite的性能在高并发场景下可能不如MySQL等服务器数据库

