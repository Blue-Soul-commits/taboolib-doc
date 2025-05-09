# IOCDatabase

## 基本信息
- 类名和包路径: taboolib.expansion.ioc.database.IOCDatabase
- 基本用途: 定义IOC容器数据存储接口
- 类型: interface
- 所属模块: database-ioc

## 类结构

### 类方法
> init(clazz: Class<*>): IOCDatabase -> 初始化容器，返回当前实例
> getDataAll(): Map<String, Any?> -> 获取所有数据，反序列化前的数据通常是String
> getData(key: String): Any? -> 获取指定键的数据
> writeData(key: String, data: Any): Boolean -> 将数据写入缓存，返回是否成功
> saveData(key: String): Unit -> 保存指定键的数据
> saveDatabase(): Unit -> 保存所有数据
> resetDatabase(): Unit -> 刷新数据源，每次writeData前会执行一次

## 实现细节
- 定义了IOC容器数据存储的标准接口
- 提供数据的读取、写入和持久化方法
- 支持单个数据操作和批量数据操作

## 使用场景
> 实现自定义数据存储方式
> 连接不同类型的数据源
> 管理IOC容器中的数据持久化

## 注意事项
> 实现类需要处理数据的序列化和反序列化
> resetDatabase方法在每次writeData前会被调用
> 实现类应确保线程安全