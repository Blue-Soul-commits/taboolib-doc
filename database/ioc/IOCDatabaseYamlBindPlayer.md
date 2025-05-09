# IOCDatabaseYamlBindPlayer

## 基本信息
- 类名和包路径: taboolib.expansion.ioc.database.impl.IOCDatabaseYamlBindPlayer
- 基本用途: 为玩家数据提供的YAML存储实现，支持玩家加入/离开服务器时自动加载/保存数据
- 类型: open class
- 所属模块: database-ioc
- 继承自: IOCDatabaseMultipleYaml

## 类结构

### 类方法
> init(clazz: Class<*>): IOCDatabase -> 初始化数据库，设置类名
> onJoinLoadData(player: UUID): Unit -> 玩家加入服务器时加载数据
> onLeaveSaveData(player: UUID): Unit -> 玩家离开服务器时保存数据

## 实现细节
- 继承自IOCDatabaseMultipleYaml，利用其多文件存储机制
- 为每个玩家创建单独的YAML文件
- 文件路径格式为"data-ioc/{类名}/{玩家UUID}.yml"
- 提供与玩家生命周期绑定的数据加载和保存方法

## 使用场景
> 需要在玩家加入服务器时加载数据
> 需要在玩家离开服务器时保存数据
> 需要为每个玩家单独存储数据
> 适用于玩家数据的IOC容器管理

## 注意事项
> 需要在玩家加入和离开事件中手动调用相应方法
> 玩家UUID作为数据文件的名称
> 继承了IOCDatabaseMultipleYaml的所有特性
> 适合管理与玩家相关的持久化数据
