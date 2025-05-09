# IOCMap

## 基本信息
- 类名和包路径: taboolib.expansion.ioc.linker.IOCMap
- 基本用途: 提供Map接口连接IOC容器，基于ConcurrentHashMap实现
- 类型: class
- 所属模块: database-ioc

## 类结构

### 类内可被访问字段
> ioc: ConcurrentHashMap<String, Any> -> 存储数据的实际容器，通过unsafeLazy加载
> database: IOCDatabase -> 数据持久化接口，默认使用IOCDatabaseYaml

### 主要方法
> put(key: String, value: Any): Any? -> 添加或更新键值对
> get(key: String): Any? -> 获取指定键的值
> remove(key: String): Any? -> 移除指定键的值
> containsKey(key: String): Boolean -> 检查是否包含指定键
> cloneIOC(): Map<String, Any> -> 创建IOC容器的副本

## 实现细节
- 继承自ConcurrentHashMap，但所有操作都委托给内部的ioc字段
- 使用unsafeLazy延迟初始化，确保只在首次访问时创建
- 通过IOCReader.dataMap获取或创建数据存储
- 通过IOCReader.databaseMap获取或创建数据库接口
- 重写了所有ConcurrentHashMap的方法，确保操作都应用于ioc字段

## 使用场景
> 需要Map风格API的IOC容器数据管理
> 需要持久化存储的键值对数据
> 需要线程安全的数据操作
> 作为IOC容器的主要数据链接器

## 注意事项
> 虽然继承自ConcurrentHashMap，但实际上是委托模式
> 所有操作都转发到内部的ioc字段
> 键必须是String类型，值必须是Any类型
> 数据会在IOCReader.write()方法中自动保存
