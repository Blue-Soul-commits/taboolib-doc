# IOCDatabaseYaml

## 基本信息
- 类名和包路径: taboolib.expansion.ioc.database.impl.IOCDatabaseYaml
- 基本用途: 实现基于单一YAML文件的IOC数据存储
- 类型: open class
- 所属模块: database-ioc

## 类结构

### 类内可被访问字段
> config: Configuration? -> YAML配置文件对象

### 类方法
> init(clazz: Class<*>): IOCDatabase -> 初始化数据库，创建YAML配置文件
> getDataAll(): Map<String, Any?> -> 获取所有数据
> getData(key: String): String? -> 获取指定键的数据
> writeData(key: String, data: Any): Boolean -> 写入数据
> saveData(key: String): Unit -> 保存数据（实际保存整个文件）
> saveDatabase(): Unit -> 保存所有数据
> resetDatabase(): Unit -> 清空数据库

## 实现细节
- 使用单一YAML文件存储所有数据
- 文件路径格式为"data-ioc/{类名}/data.yml"
- 每个数据项作为YAML文件的顶级节点
- 使用SerializationManager进行数据序列化

## 使用场景
> 作为IOC容器的默认数据存储实现
> 适用于数据量较小的场景
> 需要简单配置文件存储的场景
> 作为自定义数据库实现的基类

## 注意事项
> 所有数据存储在同一个文件中，可能导致文件过大
> saveData和saveDatabase方法都会保存整个文件
> 适合数据量小但访问频率高的场景
> 是IOCReader的默认数据库实现
