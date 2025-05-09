# IOCReader

## 基本信息
- 类名和包路径: taboolib.expansion.ioc.IOCReader
- 基本用途: IOC容器的核心管理器，负责数据读取和持久化
- 类型: object (单例)
- 所属模块: database-ioc

## 类结构

### 类内可被访问字段
> databaseMap: ConcurrentHashMap<String, IOCDatabase> -> 存储各个类型对应的数据库实现
> dataMap: ConcurrentHashMap<String, ConcurrentHashMap<String, Any>> -> 存储所有IOC管理的数据对象

### 主要方法
> readRegister(classes: List<Class<*>>, defaultIOCDatabase: IOCDatabase): Unit -> 注册并加载类列表中的IOC组件
> write(): Unit -> 将内存中的数据写入持久化存储

## 实现细节
- 使用@Inject注解标记为TabooLib注入对象
- 使用ConcurrentHashMap确保线程安全
- 通过反射和注解识别@Component标记的类
- 使用DataReadEvent允许自定义数据加载过程
- 使用SerializationManager处理对象序列化和反序列化
- 使用IndexReader获取对象的唯一标识
- 通过@Schedule注解实现定期自动保存数据

## 使用场景
> 初始化IOC容器并加载数据
> 管理多种类型的数据对象
> 提供线程安全的数据访问
> 自动持久化数据存储

## 注意事项
> 必须在应用启动时调用readRegister方法初始化容器
> 默认使用IOCDatabaseYaml作为持久化实现
> 数据会在应用关闭时自动保存(LifeCycle.DISABLE)
> 也会每2400个游戏刻自动保存一次数据
