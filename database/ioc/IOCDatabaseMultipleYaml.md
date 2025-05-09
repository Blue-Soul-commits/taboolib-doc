# IOCDatabaseMultipleYaml

## 基本信息
- 类名和包路径: taboolib.expansion.ioc.database.impl.IOCDatabaseMultipleYaml
- 基本用途: 实现基于多YAML文件的IOC数据存储
- 类型: open class
- 所属模块: database-ioc

## 类结构

### 类内可被访问字段
> config: ConcurrentHashMap<String, Configuration> -> 存储配置文件的映射
> clazz: String -> 当前处理的类名
> files: ArrayList<File> -> 存储已加载的文件列表

### 类方法
> getConfig(key: String): Configuration -> 获取或创建指定键的配置文件
> loadConfig(): Unit -> 加载所有文件到配置映射
> loadFile(file: File): Unit -> 递归加载文件或目录
> init(clazz: Class<*>): IOCDatabase -> 初始化数据库
> getDataAll(): Map<String, Any?> -> 获取所有数据
> getData(key: String): String? -> 获取指定键的数据
> writeData(key: String, data: Any): Boolean -> 写入数据
> saveData(key: String): Unit -> 保存指定键的数据并从内存中移除
> saveDatabase(): Unit -> 保存所有数据
> resetDatabase(): Unit -> 重置数据库（此实现为空操作）

## 实现细节
- 使用ConcurrentHashMap确保线程安全
- 每个数据项存储在单独的YAML文件中
- 文件路径格式为"data-ioc/{类名}/{键}.yml"
- 递归加载目录中的所有文件
- 数据存储在配置文件的"data"节点下

## 使用场景
> 需要将每个数据项存储在单独文件中时
> 处理大量数据且需要分散存储时
> 需要按需加载数据时
> 作为IOCDatabaseYamlBindPlayer的基类

## 注意事项
> 文件名（不含扩展名）作为数据的键
> saveData方法会从内存中移除配置，下次访问时重新加载
> resetDatabase方法在此实现中不执行任何操作
> 适合数据量大但访问频率低的场景

