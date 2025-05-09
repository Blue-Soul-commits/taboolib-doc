# ContainerSQLite

## 基本信息
- 类名和包路径: taboolib.expansion.ContainerSQLite
- 基本用途: 实现基于SQLite的数据容器，提供SQLite数据库表的创建功能
- 类型: 具体实现类
- 所属模块: database-ptc

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> host: HostSQLite -> SQLite数据库主机对象，用于连接SQLite数据库文件

### 类方法
> createTable(name: String, player: Boolean, playerKey: Boolean, data: List<ContainerBuilder.Data>): Table<*, *> -> 创建SQLite数据库表

## 实现细节
- 继承自Container抽象类，实现SQLite特定的表创建逻辑
- 根据player参数决定是否添加username列，用于玩家数据存储
- 根据playerKey参数决定username列是否为主键
- 根据数据列定义(ContainerBuilder.Data)自动选择适合的SQLite数据类型
- 支持整数(INTEGER)、浮点数(NUMERIC)和文本(TEXT)三种基本数据类型

## 使用场景
> 需要使用SQLite数据库存储数据的插件
> 单机环境下的数据持久化
> 不需要复杂数据库功能的简单数据存储

## 注意事项
> SQLite数据库文件需要有正确的读写权限
> 整数类型(int和long)在SQLite中都使用INTEGER类型
> 文本类型会根据指定的length设置长度，其他类型忽略length参数
> 玩家容器会自动添加username列，用于存储玩家UUID
